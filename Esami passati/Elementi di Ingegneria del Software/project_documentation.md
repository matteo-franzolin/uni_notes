# Documentazione di Progetto: ListAdapter (CLDC 1.1)

## 1. Introduzione e Contesto
Questo progetto implementa una libreria (denominata `myAdapter`) sviluppata per l'ambiente **Java Micro Edition (JME) CLDC 1.1**. Lo scopo è fornire un *Adapter* per l'interfaccia `List` (e per tutte le relative interfacce di supporto del *Java Collections Framework*), permettendo di utilizzare codice progettato originariamente per J2SE 1.4.2 all'interno di un ambiente ristretto in cui queste interfacce non sono nativamente disponibili.

Le specifiche dell'esame richiedono l'uso esclusivo di feature e classi presenti in **CLDC 1.1**. Non è consentito l'uso di Generics, Streams o classi del Java Collections Framework moderno. Tutte le classi e i metodi devono comportarsi in modo identico a quanto specificato dalla documentazione ufficiale J2SE 1.4.2.

## 2. Architettura e Design Pattern

Il design adotta il pattern architetturale **Object Adapter**. 
A differenza del *Class Adapter* (che fa uso dell'ereditarietà), l'*Object Adapter* incapsula l'istanza della classe da adattare (*adaptee*) al suo interno.

- **Target Interfaces**: `HCollection`, `HList`, `HIterator`, `HListIterator` (definite localmente nel package per evitare collisioni).
- **Adapter**: La classe `ListAdapter`, che implementa `HList` (e di conseguenza `HCollection`).
- **Adaptee**: La classe base utilizzata per la memorizzazione dei dati è `java.util.Vector`, l'unica collezione posizionale fornita dallo standard CLDC 1.1. 

Questo isolamento assicura che eventuali metodi non richiesti di `Vector` (come `capacity()` o `trimToSize()`) non inquinino il namespace e l'interfaccia pubblica del nostro Adapter.

## 3. Struttura del Package `myAdapter`

Tutti i componenti logici si trovano al primo livello del package `myAdapter` senza ulteriori nidificazioni.

### Interfacce di Supporto
* **`HCollection`**: Interfaccia radice. Fornisce i comportamenti generali della collection (aggiunta, rimozione, interrogazione su dimensione e inclusione).
* **`HList`**: Estende `HCollection`. Aggiunge i concetti di sequenza ordinata, accesso basato su indici e supporto per sotto-viste dinamiche (`subList()`).
* **`HIterator`**: Meccanismo per lo scorrimento progressivo degli elementi di una `HCollection`.
* **`HListIterator`**: Versione avanzata dell'iteratore dedicata unicamente a `HList`. Supporta l'attraversamento bidirezionale, la mutazione state-dependent e le operazioni in-place (`set`, `add`).

### Implementazioni Concrete
* **`ListAdapter`**: Implementa il nucleo logico della lista. Utilizza istruzioni come `insertElementAt`, `removeElementAt` fornite dal Vector per riprodurre le operazioni di index-shifting previste dall'API List. Tutti i metodi, incluse le iterazioni opzionali, sono integralmente supportati.
* **Iteratori Interni**: Gli iteratori `ListAdapterIterator` (per `iterator()`) e `ListAdapterListIterator` (per `listIterator()`) sono stati definiti come **Inner Classes** private all'interno di `ListAdapter`. In questo modo hanno accesso diretto e controllato allo stato della lista (ad esempio tramite la get(index)), semplificando notevolmente il meccanismo mutativo.
* **`SubList`**: Classe package-private usata per restituire viste dinamiche da `ListAdapter.subList()`. Rispetta strettamente la semantica J2SE: non crea una copia dei dati, ma implementa un **meccanismo di backing** mantenendo un riferimento al ListAdapter originale con offset spaziali (min/max bound). Le modifiche eseguite su `SubList` sono riflesse sulla ListAdapter padre e viceversa.

## 4. Gestione Eccezioni e Null Pointer
Come dettato dalla libreria Java Collections 1.4.2:
- La lista supporta l'inserimento, ricerca e cancellazione di elementi `null`.
- I controlli sui bound (`IndexOutOfBoundsException`) avvengono costantemente prima di delegare operazioni sensibili all'adaptee.
- Le chiamate mutative sugli iteratori (`remove`, `set`) sollevano correttamente una `IllegalStateException` se fatte in momenti inappropriati (es. due `remove()` consecutive senza `next()`).

> [!NOTE]
> Per requisiti specifici di esame, non è stata implementata la concorrenza (`fail-fast` o monitoraggio delle modCount) e non è stata garantita la Thread Safety.
