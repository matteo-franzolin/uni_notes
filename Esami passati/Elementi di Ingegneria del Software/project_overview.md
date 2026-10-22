# Panoramica del Progetto (Workspace Overview)

Questa è una panoramica completa della struttura del tuo progetto Java. Ti aiuterà a orientarti facilmente tra le varie cartelle, comprendere il ruolo di ogni file e seguire in modo chiaro il flusso di compilazione e di esecuzione dei test.

## Mappa ad Albero del Workspace

Ecco la rappresentazione della struttura principale della root del progetto (escludendo alcuni file generati automaticamente nella cartella `docs` e `bin` per brevità):

```text
Esame EDIDS/
├── .agents/
│   └── CLDC_11_RULES.md
├── Appello1.pdf
├── bin/
│   ├── myAdapter/
│   │   └── (File .class compilati dell'adapter)
│   └── myTest/
│       └── (File .class compilati dei test)
├── docs/
│   ├── index.html
│   ├── (Vari file HTML, CSS e JS generati da Javadoc)
│   ├── myAdapter/
│   └── myTest/
├── JUnit/
│   └── junit-3.8.1.jar
├── myAdapter/
│   ├── HCollection.java
│   ├── HIterator.java
│   ├── HList.java
│   ├── HListIterator.java
│   ├── ListAdapter.java
│   ├── SubList.java
│   └── (Eventuali file .class se compilati nella stessa cartella)
└── myTest/
    ├── IteratorTest.java
    ├── ListAdapterTest.java
    ├── ListIteratorTest.java
    ├── SubListTest.java
    ├── TestRunner.java
    └── (Eventuali file .class se compilati nella stessa cartella)
```

## Spiegazione delle Directory

Di seguito trovi una spiegazione semplice del ruolo di ogni cartella e del suo contenuto:

### 1. `.agents`
**Scopo**: Contiene file di configurazione o linee guida utilizzate dagli agenti IA per mantenere il contesto del progetto.
**Contenuto**: Troverai file come `CLDC_11_RULES.md`, che funge da promemoria sulle rigide regole e limitazioni di Java ME CLDC 1.1 e J2SE 1.4.2 da rispettare durante la scrittura del codice.

### 2. `bin` (Binaries)
**Scopo**: È la cartella di output (destinazione) designata per contenere il codice binario eseguibile.
**Contenuto**: Quando eseguiamo la compilazione separando i sorgenti dai compilati, tutti i file `.class` generati dal compilatore Java vengono posizionati qui, mantenendo la struttura dei package (`myAdapter` e `myTest`).

### 3. `docs`
**Scopo**: Ospita l'intera documentazione tecnica del progetto in formato web.
**Contenuto**: Contiene i file HTML (come `index.html`), i fogli di stile CSS e gli script JS generati automaticamente dallo strumento **Javadoc**. Aprendo `index.html` in un browser, puoi navigare comodamente tra la documentazione in italiano delle tue classi e dei tuoi test.

### 4. `JUnit`
**Scopo**: Contiene le librerie esterne necessarie per il testing del codice.
**Contenuto**: Include il file `junit-3.8.1.jar`. Questo archivio è fondamentale perché fornisce tutte le classi necessarie (come `TestCase`, `TestSuite`, `assertEquals`, ecc.) per far funzionare i nostri test in ambiente JUnit 3.

### 5. `myAdapter`
**Scopo**: È il cuore del tuo progetto, contenente il codice sorgente del tuo "Adapter".
**Contenuto**: Qui trovi i file `.java` contenenti le interfacce (`HCollection`, `HList`, ecc.) e le loro implementazioni concrete (`ListAdapter`, `SubList`). Se la compilazione avviene senza specificare una cartella di output, potresti trovare al suo interno anche i file `.class` corrispondenti.

### 6. `myTest`
**Scopo**: Contiene il codice sorgente per testare la correttezza di `myAdapter`.
**Contenuto**: Include classi `.java` che implementano i test (es. `ListAdapterTest.java`) e la classe principale `TestRunner.java` che si occupa di eseguire tutte le suite di test e stampare i risultati a schermo.

---

## Guida al Flusso di Compilazione ed Esecuzione

Quando lavori da riga di comando, è importante capire come si muovono i file. Ecco cosa succede passo passo:

### 1. Compilazione
**Comando**: `javac -cp ".;JUnit/junit-3.8.1.jar" -d bin myAdapter/*.java myTest/*.java`

* **Cosa legge il compilatore (`javac`)**: 
  Il compilatore legge tutti i file con estensione `.java` contenuti all'interno delle cartelle `myAdapter/` e `myTest/`. Legge anche il file `junit-3.8.1.jar` fornito tramite il parametro `-cp` (classpath) per capire come risolvere i riferimenti a JUnit nei file di test.
* **Dove finiscono i file generati**: 
  Grazie all'opzione `-d bin`, il compilatore inserisce tutti i file `.class` (il bytecode comprensibile dalla Java Virtual Machine) all'interno della cartella `bin`. Se una classe appartiene al package `myAdapter`, il suo file `.class` finirà in `bin/myAdapter/`.

> [!TIP]
> Separare i file `.java` (nella cartella dei sorgenti) dai file `.class` (nella cartella `bin`) è un'ottima pratica per mantenere il progetto ordinato e pulito.

### 2. Esecuzione dei Test
**Comando**: `java -cp "bin;JUnit/junit-3.8.1.jar" myTest.TestRunner`

* **Cosa fa la Java Virtual Machine (`java`)**:
  Per eseguire i test, la JVM deve leggere i file `.class` generati nel passaggio precedente.
* **Come trova i file**:
  Tramite il parametro `-cp "bin;JUnit/junit-3.8.1.jar"`, diciamo alla JVM di cercare il codice compilato all'interno della cartella `bin` e di caricare le librerie di JUnit dal file `.jar`.
* **L'esecuzione**:
  La JVM cerca la classe `myTest.TestRunner` all'interno di `bin/myTest/TestRunner.class` ed esegue il suo metodo `main()`. A questo punto, il TestRunner raccoglierà automaticamente i test compilati in `bin/myTest/`, li eseguirà usando il codice di `bin/myAdapter/`, e infine ti mostrerà il riepilogo a terminale.
