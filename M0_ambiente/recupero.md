# Recupero di file versionati per errore

## Simulazione dell'errore

```bash
mkdir M0_ambiente\temporanei
echo appunto 1 > M0_ambiente\temporanei\nota.txt
echo appunto 2 > M0_ambiente\temporanei\bozza.txt
git add M0_ambiente/temporanei
git commit -m "chore(M0_ambiente): aggiungi appunti temporanei (per errore)"
```

La cartella `temporanei` con i suoi due file viene così tracciata e
registrata in un commit, **prima** di essere inserita nel `.gitignore`.

## Aggiunta (tardiva) al `.gitignore`

```
# Cartella di appunti temporanei
M0_ambiente/temporanei/
```

## Diagnosi: il `.gitignore` da solo non basta

```bash
git status
git ls-files M0_ambiente/temporanei
git check-ignore -v M0_ambiente/temporanei/nota.txt
```

Output ottenuto:

```
$ git status
 M .gitignore

$ git ls-files M0_ambiente/temporanei
M0_ambiente/temporanei/bozza.txt
M0_ambiente/temporanei/nota.txt

$ git check-ignore -v M0_ambiente/temporanei/nota.txt
(nessun output, exit code 1)
```

`git ls-files` continua a restituire i due file: sono ancora tracciati.
Sorprendentemente, anche `git check-ignore -v` non restituisce alcuna
riga per un file **già presente nell'indice**: Git non applica le regole
di esclusione ai percorsi che sta già seguendo, perché considera
l'aggiunta esplicita (`git add`) come una decisione più forte della
regola generica del `.gitignore`. Il pattern esiste ed è corretto — lo si
può verificare forzando il confronto sul solo albero di lavoro con
`git check-ignore -v --no-index`, che infatti lo segnala:

```
$ git check-ignore -v --no-index M0_ambiente/temporanei/nota.txt
.gitignore:21:M0_ambiente/temporanei/	M0_ambiente/temporanei/nota.txt
```

## Correzione: rimozione dal tracciamento mantenendo i file su disco

```bash
git rm -r --cached M0_ambiente/temporanei
git add .gitignore
git commit -m "fix(M0_ambiente): rimuovi temporanei dal tracciamento e aggiorna .gitignore"
```

Output di `git rm -r --cached`:

```
rm 'M0_ambiente/temporanei/bozza.txt'
rm 'M0_ambiente/temporanei/nota.txt'
```

## Verifica finale

```bash
git ls-files M0_ambiente/temporanei
git check-ignore -v M0_ambiente/temporanei/nota.txt
git status
```

```
$ git ls-files M0_ambiente/temporanei
(nessuna riga)

$ git check-ignore -v M0_ambiente/temporanei/nota.txt
.gitignore:21:M0_ambiente/temporanei/	M0_ambiente/temporanei/nota.txt

$ git status
(albero di lavoro pulito)
```

I due file `nota.txt` e `bozza.txt` sono ancora presenti sul disco (la
flag `--cached` di `git rm` rimuove solo dall'indice, non dal filesystem),
ma non sono più tracciati né segnalati da Git: ora `check-ignore` li
riconosce correttamente perché, non essendo più nell'indice, tornano
soggetti alle regole del `.gitignore`.

## Perché il `.gitignore` non agisce sui file già tracciati

Il `.gitignore` dice a Git quali percorsi **ignorare quando decide cosa
proporre di aggiungere** (in `git status`, `git add -A`, negli strumenti che
suggeriscono file nuovi): agisce cioè solo sui file non ancora presenti
nell'indice. Un file aggiunto con `git add` ed eventualmente committato è
già entrato a far parte della "fotografia" versionata del progetto: da quel
momento Git lo tratta come un file da seguire a tutti gli effetti, e la
comparsa successiva del suo percorso in un `.gitignore` non ha alcun
effetto retroattivo. Per smettere di tracciarlo è necessario un comando
esplicito che agisca sull'indice, come `git rm --cached` (che lo rimuove
mantenendolo sul disco) o `git rm` (che lo rimuove anche dal disco); solo
dopo questa operazione le regole del `.gitignore` tornano ad avere effetto
su quel percorso.
