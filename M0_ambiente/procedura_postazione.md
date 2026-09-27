# Procedura di configurazione della postazione (Windows)

Procedura per portare una postazione Windows appena ripristinata allo stato
di lavoro del Modulo M0. Sostituire `<url-del-repository>` con l'indirizzo
HTTPS del repository su GitHub. Per la cartella personale si usa `$HOME`.

## 1. Installare Git
Installer da `https://git-scm.com/download/win`, opzioni predefinite.
```powershell
git --version
```
Atteso: `git version 2.4x.x.windows.1`.

## 2. Installare Python
Installer da `https://www.python.org/downloads/`, versione 3.12, con
"Add python.exe to PATH" spuntato.
```powershell
py -3.12 --version
```
Atteso: `Python 3.12.x`.

## 3. Configurare l'identità Git
```powershell
git config --global user.name "Nome Cognome"
git config --global user.email "indirizzo@example.it"
```
Verifica: `git config --global user.name`/`user.email` mostrano i valori impostati.

## 4. Clonare il repository personale
```powershell
cd $HOME
git clone <url-del-repository>
cd (Split-Path <url-del-repository> -Leaf)
git status
```
Atteso: `On branch main`, `nothing to commit, working tree clean`.

## 5. Verificare il `.gitignore`
```powershell
Get-Content .gitignore
```
Atteso: regole per `__pycache__/`, `.venv/`, `.ipynb_checkpoints/`, `Thumbs.db`, `*.tmp`.

## 6. Creare l'ambiente virtuale di prova
```powershell
cd M0_ambiente
py -3.12 -m venv .venv
cd ..
git status
git check-ignore -v M0_ambiente/.venv/pyvenv.cfg
```
Atteso: `.venv` assente da `git status`; `check-ignore -v` restituisce
file, riga e modello del `.gitignore` che lo esclude.

## 7. Attivare l'ambiente e verificare l'interprete
```powershell
M0_ambiente\.venv\Scripts\Activate.ps1
python --version
```
Atteso: prompt con prefisso `(.venv)`; `Python 3.12.x`.

## 8. Commit di prova e sincronizzazione
```powershell
"prova" | Out-File M0_ambiente\prova_postazione.md
git add M0_ambiente/prova_postazione.md
git commit -m "chore(M0_ambiente): verifica configurazione nuova postazione"
git push
git log --oneline --graph --decorate -1
```
Atteso: `HEAD -> main` e `origin/main` sullo stesso commit.

## Errori incontrati, causa e rimedio

1. **`fatal: not a git repository (or any of the parent directories)`** —
   comando eseguito fuori dalla cartella del repository. Rimedio: `cd`
   nella cartella clonata.
2. **`fatal: unable to auto-detect email address`** al primo commit —
   identità Git non configurata. Rimedio: eseguire il punto 3 prima del
   primo commit.
3. **`! [rejected] main -> main (fetch first)`** al `git push` — il
   remoto conteneva commit assenti in locale. Rimedio: `git pull` (merge
   o rebase), poi ripetere `git push`.
4. **File di `M0_ambiente/temporanei` restati tracciati** dopo averli
   aggiunti al `.gitignore` — non è retroattivo sui percorsi già
   nell'indice. Rimedio: `git rm -r --cached <percorso>`, poi commit.
5. **`'py' non è riconosciuto come comando interno o esterno`** — Python
   installato senza aggiungerlo al `PATH`. Rimedio: reinstallare con
   l'opzione attiva o aggiungerlo manualmente, poi riaprire il terminale.
