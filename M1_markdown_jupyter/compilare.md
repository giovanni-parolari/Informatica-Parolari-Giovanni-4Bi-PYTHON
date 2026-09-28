### Svolgimento

I sorgenti sono in `src/`, la compilazione va in `bin/` e la classe con il metodo `main` si chiama `MediaVoti`.

1. **Clonare il repository** ed entrare nella cartella:

```powershell
   git clone https://github.com/utente/nome-repository.git
   cd nome-repository
```

2. **Verificare il JDK**:
   - eseguire `javac -version` per il compilatore;
   - eseguire `java -version` per l'ambiente di esecuzione.

3. **Compilare** con l'opzione `-d` per generare i file `.class` nella cartella `bin/`:

```powershell
   mkdir -p bin
   javac -d bin src/*.java
```

4. **Eseguire** la classe `MediaVoti` con l'opzione `-cp` puntata a `bin/`:

```powershell
   java -cp bin MediaVoti
```

5. **Controllare l'output** nel terminale; in caso di errori, verificare i percorsi di `src/` e `bin/`.
