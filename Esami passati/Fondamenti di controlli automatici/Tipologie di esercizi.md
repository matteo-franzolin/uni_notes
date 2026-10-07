## 1. Modellistica e Analisi nello Spazio di Stato

Questo macroargomento si concentra sulla scrittura delle equazioni differenziali (o alle differenze) che governano un sistema fisico/informatico e sullo studio delle sue proprietà strutturali intrinseche.

- **Sistemi Meccanici, Idraulici ed Elettrici (Tempo Continuo):**
    
    - Scrivere le equazioni della dinamica del sistema in forma di spazio di stato (es. posizioni/velocità come variabili di stato)Scrivere le equazioni della dinamica del sistema in forma di spazio di stato (es. posizioni/velocità come variabili di stato)Scrivere le equazioni della dinamica del sistema in forma di spazio di stato (es. posizioni/velocità come variabili di stato)Scrivere le equazioni della dinamica del sistema in forma di spazio di stato (es. posizioni/velocità come variabili di stato).
        
    - Trovare una rappresentazione in forma di stato a partire da uno schema circuitale (con specifiche uscite, come la tensione ai capi di un condensatore).
        
    - Determinare i punti di equilibrio del sistema (con ingressi costanti)Determinare i punti di equilibrio del sistema (con ingressi costanti)Determinare i punti di equilibrio del sistema (con ingressi costanti)**punti di equilibrio**.
        
    - **Linearizzare**Linearizzare un sistema non lineare nell'intorno dei suoi punti di equilibrioLinearizzare un sistema non lineare nell'intorno dei suoi punti di equilibrioLinearizzare un sistema non lineare nell'intorno dei suoi punti di equilibrio.
        
- **Sistemi a Eventi / Compartimentali (Tempo Discreto):**
    
    - Rappresentare processi compartimentali (es. gestione di operazioni in un computer, catene di produzione industriale, reti di pagine web) tramite grafi orientatiRappresentare processi compartimentali (es. gestione di operazioni in un computer, catene di produzione industriale, reti di pagine web) tramite grafi orientatiRappresentare processi compartimentali (es. gestione di operazioni in un computer, catene di produzione industriale, reti di pagine web) tramite grafi orientati**grafi orientati**.
        
    - Scrivere le equazioni dinamiche di stato in forma sia lineare che matricialeScrivere le equazioni dinamiche di stato in forma sia lineare che matricialeScrivere le equazioni dinamiche di stato in forma sia lineare che matriciale.
        
    - Ricavare e verificare le condizioni necessarie e sufficienti per l'esistenza di un equilibrio non negativoRicavare e verificare le condizioni necessarie e sufficienti per l'esistenza di un equilibrio non negativo.
        
    - Calcolare lo stato di equilibrio o vettori di probabilità stazionari (es. PageRank)**PageRank**.
        

## 2. Studio della Stabilità

La stabilità viene analizzata sotto diversi punti di vista (interna ed esterna) sia per sistemi a tempo continuo che a tempo discreto.

- **Analisi della Stabilità Interna (Asintotica e Marginale):**
    
    - Analizzare la stabilità asintotica calcolando gli autovalori della matrice di stato A (verificando che abbiano parte reale negativa per il tempo continuo o modulo minore di uno per il tempo discreto)Analizzare la stabilità asintotica calcolando gli autovalori della matrice di stato A (verificando che abbiano parte reale negativa per il tempo continuo o modulo minore di uno per il tempo discreto)Analizzare la stabilità asintotica calcolando gli autovalori della matrice di stato A (verificando che abbiano parte reale negativa per il tempo continuo o modulo minore di uno per il tempo discreto)**autovalori**.
        
    - Discutere la stabilità di sistemi linearizzati o descrivere qualitativamente il moto in prossimità dell'equilibrio in assenza di attriti/smorzamenti (presenza di poli puramente immaginari)Discutere la stabilità di sistemi linearizzati o descrivere qualitativamente il moto in prossimità dell'equilibrio in assenza di attriti/smorzamenti (presenza di poli puramente immaginari)Discutere la stabilità di sistemi linearizzati o descrivere qualitativamente il moto in prossimità dell'equilibrio in assenza di attriti/smorzamenti (presenza di poli puramente immaginari).
        
    - Applicare il Criterio di Routh su polinomi caratteristici dipendenti da un parametro K per determinare i range di stabilitàApplicare il Criterio di Routh su polinomi caratteristici dipendenti da un parametro K per determinare i range di stabilitàApplicare il Criterio di Routh su polinomi caratteristici dipendenti da un parametro K per determinare i range di stabilità**Criterio di Routh**.
        
- **Analisi della Stabilità Esterna:**
    
    - Valutare la stabilità BIBS (Bounded Input Bounded State) e BIBO (Bounded Input Bounded Output)Valutare la stabilità BIBS (Bounded Input Bounded State) e BIBO (Bounded Input Bounded Output)**BIBS**_Bounded Input Bounded State_**BIBO**_Bounded Input Bounded Output_.
        
    - Fornire controesempi fisici (es. ingressi limitati come il gradino che generano uscite illimitate) nel caso in cui un sistema risulti instabileFornire controesempi fisici (es. ingressi limitati come il gradino che generano uscite illimitate) nel caso in cui un sistema risulti instabile.
        

## 3. Calcolo della Risposta Temporale (Evoluzione dei Sistemi)

In questa categoria rientrano i problemi in cui si richiede di calcolare matematicamente come variano lo stato o l'uscita nel tempo a fronte di particolari ingressi o condizioni iniziali.

- **Sistemi a Tempo Continuo (Trasformata di Laplace):**
    
    - Calcolare l'evoluzione libera (dovuta alle sole condizioni iniziali) e la risposta forzata (dovuta al solo ingresso, es. gradino, seno o coseno)Calcolare l'evoluzione libera (dovuta alle sole condizioni iniziali) e la risposta forzata (dovuta al solo ingresso, es. gradino, seno o coseno)Calcolare l'evoluzione libera (dovuta alle sole condizioni iniziali) e la risposta forzata (dovuta al solo ingresso, es. gradino, seno o coseno)Calcolare l'evoluzione libera (dovuta alle sole condizioni iniziali) e la risposta forzata (dovuta al solo ingresso, es. gradino, seno o coseno)Calcolare l'evoluzione libera (dovuta alle sole condizioni iniziali) e la risposta forzata (dovuta al solo ingresso, es. gradino, seno o coseno)**evoluzione libera****risposta forzata**.
        
    - Determinare la risposta complessiva come somma dei due contributi precedentiDeterminare la risposta complessiva come somma dei due contributi precedenti.
        
    - Esprimere l'andamento temporale separando la componente transitoria dalla componente permanente (a regime)Esprimere l'andamento temporale separando la componente transitoria dalla componente permanente (a regime)Esprimere l'andamento temporale separando la componente transitoria dalla componente permanente (a regime)Esprimere l'andamento temporale separando la componente transitoria dalla componente permanente (a regime)**componente transitoria****componente permanente (a regime)**.
        
    - Calcolare il periodo o la pulsazione del segnale d'uscita a regime quando l'ingresso è sinusoidale (sfruttando le proprietà dei sistemi LTI)Calcolare il periodo o la pulsazione del segnale d'uscita a regime quando l'ingresso è sinusoidale (sfruttando le proprietà dei sistemi LTI)Calcolare il periodo o la pulsazione del segnale d'uscita a regime quando l'ingresso è sinusoidale (sfruttando le proprietà dei sistemi LTI).
        
- **Sistemi a Tempo Discreto (Trasformata Z):**
    
    - Calcolare l'evoluzione temporale libera e forzata dello stato utilizzando la trasformata ZCalcolare l'evoluzione temporale libera e forzata dello stato utilizzando la trasformata ZCalcolare l'evoluzione temporale libera e forzata dello stato utilizzando la trasformata ZCalcolare l'evoluzione temporale libera e forzata dello stato utilizzando la trasformata Z.
        
    - Analizzare l'andamento dei singoli modi naturali del sistema (es. identificare se un modo è divergente, convergente, oscillatorio o alternante)Analizzare l'andamento dei singoli modi naturali del sistema (es. identificare se un modo è divergente, convergente, oscillatorio o alternante)**modi naturali**.
        
    - Calcolare il valore di regime (limite per k \to \infty) dello stato o di funzioni dello stato a transitorio esauritoCalcolare il valore di regime (limite per k \to \infty) dello stato o di funzioni dello stato a transitorio esauritoCalcolare il valore di regime (limite per k \to \infty) dello stato o di funzioni dello stato a transitorio esaurito**valore di regime**.
        

## 4. Sintesi dei Controllori e Luogo delle Radici

Questo blocco riguarda la progettazione di sistemi di controllo in retroazione unitaria (negativa) per soddisfare requisiti industriali standard.

- **Tracciamento del Luogo delle Radici:**
    
    - Tracciare il comportamento dei poli a ciclo chiuso al variare del guadagno K \ge 0Tracciare il comportamento dei poli a ciclo chiuso al variare del guadagno K \ge 0Tracciare il comportamento dei poli a ciclo chiuso al variare del guadagno K \ge 0.
        
    - Determinare analiticamente: asintoti (numero, angoli e baricentro), punti doppi/multipli (di distacco o attacco sull'asse reale) e punti di intersezione con l'asse immaginario con i rispettivi valori critici di guadagno KDeterminare analiticamente: asintoti (numero, angoli e baricentro), punti doppi/multipli (di distacco o attacco sull'asse reale) e punti di intersezione con l'asse immaginario con i rispettivi valori critici di guadagno KDeterminare analiticamente: asintoti (numero, angoli e baricentro), punti doppi/multipli (di distacco o attacco sull'asse reale) e punti di intersezione con l'asse immaginario con i rispettivi valori critici di guadagno KDeterminare analiticamente: asintoti (numero, angoli e baricentro), punti doppi/multipli (di distacco o attacco sull'asse reale) e punti di intersezione con l'asse immaginario con i rispettivi valori critici di guadagno K**asintoti****punti doppi/multipli****intersezione con l'asse immaginario**.
        
- **Progettazione del Controllore (Sintesi Integrale, PI o Proporzionale):**
    
    - Progettare un controllore (es. puramente Integrale \mathcal{C}(s) = \frac{k_i}{s} o Proporzionale-Integrale PI) in grado di garantire un errore a regime nullo in risposta a un ingresso a gradino unitarioProgettare un controllore (es. puramente Integrale \mathcal{C}(s) = \frac{k_i}{s} o Proporzionale-Integrale PI) in grado di garantire un errore a regime nullo in risposta a un ingresso a gradino unitarioProgettare un controllore (es. puramente Integrale \mathcal{C}(s) = \frac{k_i}{s} o Proporzionale-Integrale PI) in grado di garantire un errore a regime nullo in risposta a un ingresso a gradino unitarioProgettare un controllore (es. puramente Integrale \mathcal{C}(s) = \frac{k_i}{s} o Proporzionale-Integrale PI) in grado di garantire un errore a regime nullo in risposta a un ingresso a gradino unitario**errore a regime nullo**.
        
    - Tarare i parametri del controllore (k_p, k_i) posizionando i poli dominanti sul piano complesso per soddisfare vincoli dinamici specifici: sovraelongazione massima (M_p\%) e tempo di assestamento (T_s)Tarare i parametri del controllore (k_p, k_i) posizionando i poli dominanti sul piano complesso per soddisfare vincoli dinamici specifici: sovraelongazione massima (M_p\%) e tempo di assestamento (T_s)Tarare i parametri del controllore (k_p, k_i) posizionando i poli dominanti sul piano complesso per soddisfare vincoli dinamici specifici: sovraelongazione massima (M_p\%) e tempo di assestamento (T_s)Tarare i parametri del controllore (k_p, k_i) posizionando i poli dominanti sul piano complesso per soddisfare vincoli dinamici specifici: sovraelongazione massima (M_p\%) e tempo di assestamento (T_s)**sovraelongazione massima****tempo di assestamento**.
        
    - Discutere se l'utilizzo di altre strutture di controllo (es. proporzionale-derivativa PD) possa o meno soddisfare le specifiche sull'errore staticoDiscutere se l'utilizzo di altre strutture di controllo (es. proporzionale-derivativa PD) possa o meno soddisfare le specifiche sull'errore statico.
        
- **Analisi della Risposta a Ciclo Chiuso:**
    
    - Trovare poli e zeri della funzione di trasferimento a ciclo chiuso W(s).
        
    - Determinare l'effetto dello spostamento degli zeri della f.d.t. (dovuto al cambio dei parametri del controllore) sulla rapidità e sulla sovraelongazione della risposta al gradino.
        
    - Ricavare le unità di misura coerenti dei parametri del controllore (k_p, k_i) basandosi sulle unità delle grandezze fisiche di ingresso e uscita del processo**unità di misura coerenti**.