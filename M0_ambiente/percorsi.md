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
'''python
nome = "Mario" 
postazione = 14

# Stampa la riga di saluto formattata
print(f"Ciao, sono {nome} e sto lavorando dalla postazione numero {postazione}!")
'''