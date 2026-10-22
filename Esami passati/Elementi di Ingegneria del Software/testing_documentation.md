# Documentazione Strategia di Testing TDD: ListAdapter

## 1. Strategia Generale
Lo sviluppo è stato guidato interamente dalla metodologia **Test Driven Development (TDD)** utilizzando il framework **JUnit 3.8.1**. Le specifiche della consegna richiedevano la redazione di casi di test completi per l'infrastruttura dell'Adapter *prima* dell'effettiva finalizzazione del codice sorgente di produzione, seguendo il ciclo "Red, Green, Refactor".

- Le librerie di test vivono isolatamente nel package `myTest`.
- L'esecuzione dei test, demandata alla classe aggregatrice `TestRunner`, produce un verboso output utile in contesti di *Continuous Integration* da terminale, non dipendente da IDE e facilmente invocabile dal comando CLI `java`.
- **Compatibilità limitata**: Dato il target pre-Java 5, l'infrastruttura estende in modo puramente Object-Oriented la classe base di JUnit (`TestCase`), sfruttando il metodo `setUp()` per l'inizializzazione e tralasciando completamente pattern successivi come l'annotation `@Test` e i Generics.

## 2. Template di Documentazione

Tutti i commenti nel codice (codificati in blocchi Javadoc standard) aderiscono rigidamente ai template definiti nell'assegnamento (Homework Templates):

* **A livello di Class (`Test Case Section`)**:
  - `Summary`: Descrizione esauriente dello scopo del file di test.
  - `Test Case Design`: Categorizzazione e logica d'organizzazione metodologica dietro al test file.

* **A livello di Method (`Test Method Section`)**:
  - `Summary`: Scopo diretto dell'azione testata dal singolo metodo.
  - `Test Method Design`: Condizioni strutturali, configurazione dei confini e pre-impostazione logica del test.
  - `Pre-Condition`: Stato richiesto alla lista o agli iteratori prima dell'azione.
  - `Post-Condition`: Stato in cui dovrà imperativamente trovarsi il sistema dopo il successo.
  - `Expected Results`: Valore specifico (es. booleano, riferimento o throw d'eccezione) esaminato con la serie di *assertions*.

## 3. Suddivisione delle Test Suite (86 Test Totali)

### `ListAdapterTest` (35 Metodi)
Verifica in via esaustiva il comportamento primario della ListAdapter per le funzionalità dell'API J2SE 1.4.2 List e Collection. Include:
* Costruttori e inizializzazioni (*EmptyConstructor*).
* Edge-cases per posizioni (inserimento all'inizio, nel mezzo, alla fine, fuori limite).
* Risposta con elementi *Null*.
* Operazioni mutative singole (`add`, `set`, `remove`) ed in bulk (`addAll`, `retainAll`, `removeAll`, `containsAll`).
* Corretto calcolo dei contratti di semantica *HashCode* ed *Equals* confrontando liste create in sequenze non identiche ma omogenee in termini di risultato.

### `IteratorTest` (9 Metodi)
Analizza il `HIterator` generato nativamente dalla Root List. Punti focali:
* Traversamento standard da 0 a Size, e validazione per list vuote.
* Lancio sistematico dell'eccezione `NoSuchElementException` se invocato oltre il termine.
* Controllo approfondito dello state-machine per l'optional operation `remove()` (es. lancio `IllegalStateException` se chiamato prima del fetch `next()` o per due volte di seguito).

### `ListIteratorTest` (18 Metodi)
Si concentra sul navigatore esteso della list (`HListIterator`). Aggiunge alle logiche dell'iteratore classico una serie di vincoli più complessi:
* Inizializzazione corretta in base alla factory con index (`listIterator(index)`).
* Tracciamento del puntatore precedente e calcolo accurato di `previousIndex` e `nextIndex`.
* Bidirezionalità simultanea, e validazione delle operazioni in-place `add(Object)` e `set(Object)`.

### `SubListTest` (24 Metodi)
Fornisce l'analisi più critica dell'architettura per la feature delle `views` supportate dal SubList. Test garantiti per:
* **Backing Meccanico Bidirezionale**: Testati specificamente due set di regole. Modifiche apportate da `subList` devono vedersi nel parent (`testBackingSubToParent`). Alterazioni del set originale entro i bound devono vedersi dentro il SubList (`testBackingParentToSub`).
* Analisi di *shift index*: Un `add` nel mezzo della sub-list sfasa correttamente gli elementi della porzione restante della parent list che risiedono oltre la fine del bound.
* Contenimento stretto: Il costrutto `contains(Object)` fallisce e ignora gli elementi se esistono unicamente fuori dal perimetro delimitato.

## 4. Analisi dei Risultati

La compilazione (*Javac*) e l'esecuzione manuale a riga di comando riportano sistematicamente il seguente stato, che ratifica il completamento dell'impianto:

```
========================================
       ListAdapter Test Results
========================================
Tests run:    86
Failures:     0
Errors:       0
Time elapsed: 35 ms
========================================
ALL TESTS PASSED!
```
