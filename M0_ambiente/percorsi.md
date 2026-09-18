# Esercizio 1 — Scheda delle versioni della postazione

### Comandi
```bash
py --version
code --version
git --version
```

### Risultato
```text
Python 3.14.7

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
```text
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

