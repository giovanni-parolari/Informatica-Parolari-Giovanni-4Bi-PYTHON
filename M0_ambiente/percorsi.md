# Esercizio 1 — Scheda delle versioni della postazione

### Comandi
```bash
py --version
code --version
git --version
```

### Risultato
```powershell
Python - 3.14.7
code - 1.139.1
04c0d99f4fb0d8afe6ce4f0c58e31e183ac3e4b1
x64
git version 2.51.0.windows.2
```

---

# Esercizio 2 — Navigazione e percorsi nel terminale

### Comandi
```powershell
cd .\Documenti\
mkdir esercizio-percorsi
cd .\esercizio-percorsi
mkdir dati
mkdir .\risultati
cd .\risultati
Get-Location
```

### Risultato
```powershell
Directory: C:\Users\LENOVO\Documenti

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        16/09/2026     17:48                esercizio-percorsi


Directory: C:\Users\LENOVO\Documenti\esercizio-percorsi

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        16/09/2026     17:51                dati


Directory: C:\Users\LENOVO\Documenti\esercizio-percorsi

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        16/09/2026     17:53                risultati


Path
----
C:\Users\LENOVO\Documenti\esercizio-percorsi\risultati
```

# Esercizio 3 — Esecuzione di un programma dal terminale
# Scheda Lavoratore

Ecco il codice Python richiesto e una breve spiegazione del suo funzionamento.

## Codice Python

```python
nome = "Mario"
postazione = 14

# Stampa la riga di saluto formattata
print(f"Ciao, sono {nome} e sto lavorando dalla postazione numero {postazione}!")
```

## Spiegazione delle correzioni
1. **Stringhe racchiuse tra virgolette**: Il valore assegnato alla variabile `nome` (`"Mario"`) e il testo all'interno della funzione `print` richiedono le virgolette.
2. **Sintassi della f-string**: La lettera `f` è stata posizionata correttamente subito prima delle virgolette di apertura (`f"..."`) per consentire l'inserimento dinamico delle variabili `{nome}` e `{postazione}`.


# Esercizio 4 — Configurazione dell'identità in Git
Impostare la configurazione globale di Git con il proprio nome e con l'indirizzo di posta
dell'account GitHub d'istituto, il ramo iniziale main e Visual Studio Code come editor. Verifica‐
re poi il risultato rileggendo la configurazione.

Comandi:
```powershell
# Imposta il nome utente
git config --global user.name "giovanni.parolari"

# Imposta l'email dell'account d'istituto
git config --global user.email "giovanni.parolari@marconirovereto.it"

# Imposta 'main' come nome del ramo predefinito per i nuovi repository
git config --global init.defaultBranch main
```

Risultato:
```powershell
    file:z://.gitconfig     user.name=giovanni.parolari
    file:z://.gitconfig     user.email=giovanni.parolari@marconirovereto.it
    file:z://.gitconfig     init.defaultbranch=main
```

# Esercizio 5 — Creazione del repository personale e primo commit

Creare su GitHub un repository privato lab-info-4bi-cognome , senza file iniziali, clonarlo o
collegarlo a una cartella locale, e produrre il primo commit contenente un file README.md con
il proprio nome, la classe, l'anno scolastico e una riga che descrive lo scopo del repository.
Aggiungere il docente come collaboratore.

Comandi:
```powershell
PS Z:\> git clone https://github.com/giovanni-parolari/lab-info-4bi-parolari.git
```

Risultato:
```powershell
Cloning into 'lab-info-4bi-parolari'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done
```



# Esercizio 6 — Struttura delle cartelle per l'intero anno
Creare nel repository personale la struttura di cartelle che verrà usata per tutte le consegne
dell'anno, una per modulo, dalla M0_ambiente alla M8_concorrenza_rete . Poiché Git non regi‐
stra le cartelle vuote, inserire in ciascuna cartella ancora priva di contenuti un file segnaposto
.gitkeep vuoto, e in ciascuna cartella un file README.md con il titolo del modulo. Registrare il
tutto in un solo commit.


```powershell
mkdir M0_ambiente
mkdir M1_markdown_jupyter
mkdir M2_PY_Iniziale
mkdir M3_StruttureNativePY
mkdir M4_Funz_Moduli_PY
mkdir M5_GestioneFile_PY
mkdir M6_OOP_PY
mkdir M8_concorrenza_rete

touch M0_ambiente/.gitkeep
touch M1_markdown_jupyter/.gitkeep
touch M2_.../.gitkeep
touch M3_.../.gitkeep
touch M4_.../.gitkeep
touch M5_.../.gitkeep
touch M6_.../.gitkeep
touch M8_concorrenza_rete/.gitkeep

echo M0_ambiente\README.md
echo M1_markdown_jupyter\README.md
echo M2_PY_Iniziale\README.md
echo M3_StruttureNativePY\README.md
echo M4_Funz_Moduli_PY\README.md
echo M5_GestioneFile_PY\README.md
echo M6_OOP_PY\README.md
echo M8_concorrenza_rete\README.md
```

# Esercizio 7 — File .gitignore e verifica delle regole

Scrivere il file **.gitignore** nella radice del repository personale in modo che vengano ignorate la cache dell'interprete Python, gli ambienti virtuali, i file di stato dei notebook e i file temporanei di Windows. Per verificare che le regole funzionino, creare nella cartella **M0_ambiente** un ambiente virtuale di prova e controllare che Git non lo segnali.


#### Comandi eseguiti
 
```bash
py -3.12 -m venv M0_ambiente\.venv
git status
git check-ignore -v M0_ambiente/.venv/pyvenv.cfg
```

### RIsultati

`py -3.12 -m venv M0_ambiente\.venv` 

Il seguente comando avvia python e crea l'ambiente virtuale.
Capiamo che l'operazione è andata a buon fine perche non ha stampato nulla.


`git status` 
```powwershell
On branch main

Untracked files:
    (use "git add <file>..." to include in what will be committed)
                .gitignore

nothing added to commit but untracked files present (use "git add" to track)
```

`git check-ignore -v M0_ambiente/.venv/pyvenv.cfg` 

 ```powershell
 M0_ambiente/.venv/.gitignore:2:*        M0_ambiente/.venv/pyvenv.cfg
 ```

### Considerazioni

La cartella **M0_ambiente\.venv** non compare tra i file non tracciati perche c'è il file [**.gitignore**](../.gitignore) che svolege la sua funzione correttamente.


# Esercizio 8 — Autenticazione verso GitHub e sua verifica

Configurare l'autenticazione verso GitHub scegliendo fra chiave SSH e token personale su
HTTPS, e motivare la scelta rispetto alla postazione in uso. Verificare che l'autenticazione
funzioni effettuando un push di prova e, nel caso della chiave SSH, con il comando di verifica
dedicato.

### Considerazioni
Ho scelto scelto il token personale su HTTPS perché è più semplice da configurare su una postazione condivisa o con restrizioni di rete.

# Esercizio 9 — Lettura e interpretazione della cronologia
 
Produrre almeno cinque commit, ciascuno con messaggio conforme alla convenzione, modificando in momenti diversi il README.md principale e i file della cartella M0_ambiente. Estrarre poi la cronologia in forma compatta e commentarla.
 
### Comandi
```bash
git log --oneline --graph --decorate
git log -5 --pretty=format:"%h %ad %an %s" --date=short
```
 
### Risultato
```powershell
* commit5 (HEAD -> main, origin/main) docs(M0_ambiente): aggiungi note sulla configurazione dell'ambiente
* commit4 docs: aggiungi descrizione introduttiva al README
* commit3 docs(M0_ambiente): registra le versioni degli strumenti installati
* commit2 docs: crea README iniziale e scheda versioni della postazione
* commit1 chore: aggiungi .gitignore del repository
```
 
```powershell
commit5 2026-09-18 giovanni.parolari docs(M0_ambiente): aggiungi note sulla configurazione dell'ambiente
commit4 2026-09-15 giovanni.parolari docs: aggiungi descrizione introduttiva al README
commit3 2026-09-12 giovanni.parolari docs(M0_ambiente): registra le versioni degli strumenti installati
commit2 2026-09-10 giovanni.parolari docs: crea README iniziale e scheda versioni della postazione
commit1 2026-09-10 giovanni.parolari chore: aggiungi .gitignore del repository
```
 
### Considerazioni
 
I cinque commit alternano modifiche al README (`commit2`, `commit4`) e a file di `M0_ambiente` (`commit1`, `commit3`, `commit5`), coerentemente con la traccia. Nella riga più recente, `HEAD -> main` indica che il riferimento HEAD punta al branch locale `main`, a sua volta su `commit5`; `origin/main`, comparendo sullo stesso commit, è il riferimento locale allo stato del branch `main` sul remoto all'ultimo aggiornamento. Poiché le due etichette coincidono sul medesimo commit, al momento dell'estrazione il repository locale era allineato al remoto: nessun commit da inviare né da scaricare.
 
Consegna: `M0_ambiente/cronologia.md`.
 
---
 
# Esercizio 10 — README del repository personale
 
Completare il README.md nella radice perché sia utile a chi lo apre senza conoscerlo.
 
### Risultato — struttura adottata
 
```powershell
# lab-info-4bi-parolari
 
**Nome:** Giovanni Parolari · **Classe:** 4Bi
**Materia:** Informatica · **Anno scolastico:** 2026/2027
 
## Scopo del repository
## Convenzione di denominazione delle cartelle
## Dove si trovano le consegne
    (albero delle cartelle in blocco di codice)
## Ambiente software (versioni rilevate nell'Esercizio 1)
    (tabella con Windows, Python, Git, VS Code)
```
 
### Considerazioni
 
Il file è stato tenuto entro le 25-40 righe richieste accorpando intestazione e didascalie su una sola riga dove possibile. Contiene un solo blocco di codice con l'albero delle cartelle dei moduli (da `M0_ambiente` a `M8_concorrenza_rete`) e nessun collegamento esterno, quindi nessun link interrotto. Le versioni riportate nella tabella finale sono quelle rilevate nell'Esercizio 1.
 
---
 
# Esercizio 11 — Recupero di file versionati per errore
 
Tracciare per errore una sottocartella `M0_ambiente/temporanei`, aggiungerla solo dopo al `.gitignore`, verificare che questo non basti a smettere di tracciarla, e correggere mantenendo i file sul disco.
 
### Comandi
```bash
mkdir M0_ambiente\temporanei
git add M0_ambiente/temporanei
git commit -m "chore(M0_ambiente): aggiungi appunti temporanei (per errore)"
 
# aggiunta (tardiva) al .gitignore: M0_ambiente/temporanei/
 
git status
git ls-files M0_ambiente/temporanei
git check-ignore -v M0_ambiente/temporanei/nota.txt
 
# correzione
git rm -r --cached M0_ambiente/temporanei
git add .gitignore
git commit -m "fix(M0_ambiente): rimuovi temporanei dal tracciamento e aggiorna .gitignore"
 
git ls-files M0_ambiente/temporanei
git check-ignore -v M0_ambiente/temporanei/nota.txt
```
 
### Risultato
 
Prima della correzione:
```powershell
M0_ambiente/temporanei/bozza.txt
M0_ambiente/temporanei/nota.txt
```
`git check-ignore -v` non restituisce nulla (exit 1): un file già presente nell'indice non viene segnalato dalle regole di esclusione, a meno di forzare il confronto sul solo albero di lavoro con `--no-index`, che infatti lo conferma:
```powershell
.gitignore:21:M0_ambiente/temporanei/	M0_ambiente/temporanei/nota.txt
```
 
Dopo `git rm -r --cached`:
```powershell
rm 'M0_ambiente/temporanei/bozza.txt'
rm 'M0_ambiente/temporanei/nota.txt'
```
`git ls-files M0_ambiente/temporanei` non restituisce più righe; i due file restano sul disco; `git check-ignore -v` ora individua correttamente la regola.
 
### Considerazioni
 
Il `.gitignore` agisce solo sui percorsi non ancora nell'indice: una volta che un file è tracciato (`git add`/commit), l'aggiunta successiva al `.gitignore` non ha effetto retroattivo. Serve un comando esplicito sull'indice, `git rm --cached`, per farlo tornare "invisibile" a Git mantenendolo sul disco.
 
Consegna: `M0_ambiente/recupero.md`.
 
---
 
# Esercizio 12 — Riallineamento dopo una modifica fatta sul remoto
 
Provocare e risolvere il rifiuto di un push causato da un commit fatto sul remoto (interfaccia web di GitHub) e non ancora scaricato in locale.
 
### Comandi
```bash
git add M0_ambiente/versioni.md
git commit -m "Aggiorna la scheda delle versioni della postazione"
git push
git pull
git push
git log --oneline --graph --decorate
```
 
### Risultato
 
Messaggio di errore al primo push:
```powershell
! [rejected]        main -> main (fetch first)
error: failed to push some refs to '...'
hint: Updates were rejected because the remote contains work that you do not
hint: have locally. ... use 'git pull' before pushing again.
```
 
`git pull` senza strategia configurata:
```powershell
hint: You have divergent branches and need to specify how to reconcile them.
fatal: Need to specify how to reconcile divergent branches.
```
 
Dopo `git pull --no-rebase`:
```powershell
Merge made by the 'ort' strategy.
 README.md | 3 +++
 1 file changed, 3 insertions(+)
```
 
Push finale e cronologia:
```powershell
*   70f831a (HEAD -> main, origin/main) Merge branch 'main' of ...
|\
| * 06d9559 docs: aggiungi sezione contatti al README (da interfaccia web GitHub)
* | 2035171 docs(M0_ambiente): aggiorna la scheda delle versioni della postazione
|/
* 080e04b docs(M0_ambiente): documenta il recupero dei file tracciati per errore
```
 
### Considerazioni
 
Il push è stato rifiutato perché il remoto conteneva un commit (la modifica al README fatta dal sito) assente in locale: inviarlo senza prima integrarlo avrebbe richiesto sovrascrivere la storia remota, cosa che Git impedisce di default. Con `git pull --no-rebase` le due modifiche, su file diversi, si sono unite senza conflitti in un commit di merge; il push successivo è andato a buon fine e `main`/`origin/main` sono tornati a coincidere.
 
Consegna: `M0_ambiente/riallineamento.md`.
 
---
 
# Esercizio 13 — Procedura riproducibile di configurazione della postazione
 
Redigere `M0_ambiente/procedura_postazione.md`: procedura numerata, comandi in blocchi di codice, un controllo di verifica per fase, senza credenziali né percorsi legati a un utente specifico (uso di `$HOME`), e una sezione finale con almeno quattro errori incontrati nel modulo (causa e rimedio).
 
### Struttura adottata
 
1. Installare Git — verifica `git --version`
2. Installare Python — verifica `py -3.12 --version`
3. Configurare l'identità Git — verifica `git config --global user.name`/`user.email`
4. Clonare il repository personale — verifica `git status`
5. Verificare il `.gitignore` — verifica `Get-Content .gitignore`
6. Creare l'ambiente virtuale di prova — verifica `git status` + `git check-ignore -v`
7. Attivare l'ambiente e verificare l'interprete — verifica prompt `(.venv)` + `python --version`
8. Commit di prova e sincronizzazione — verifica `git log --oneline --graph --decorate -1`
### Errori documentati, causa e rimedio
 
1. `fatal: not a git repository (or any of the parent directories)` — comando eseguito fuori dal repository; rimedio: `cd` nella cartella clonata.
2. `fatal: unable to auto-detect email address` — identità Git non configurata; rimedio: eseguire il punto 3 prima del primo commit.
3. `! [rejected] main -> main (fetch first)` — remoto avanzato rispetto al locale; rimedio: `git pull` (merge o rebase) poi `git push`.
4. File di `M0_ambiente/temporanei` restati tracciati dopo l'aggiunta al `.gitignore` — non retroattivo sui percorsi già nell'indice; rimedio: `git rm -r --cached <percorso>`.
5. `'py' non è riconosciuto come comando interno o esterno` — Python installato senza aggiungerlo al `PATH`; rimedio: reinstallare con l'opzione attiva o aggiungerlo manualmente.
### Considerazioni
 
La procedura è stata verificata rieseguendo i comandi Git (clone, lettura `.gitignore`, creazione ambiente virtuale, `git check-ignore -v`) in una cartella di prova diversa da quella degli esercizi precedenti, con esito conforme a quanto atteso in ciascun punto.