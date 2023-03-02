# Gestione della memoria
```toc
```
--- 

Una componente importante dell'interprete di una macchina astratta è quella che si occupa della gestione della memoria.

## Tipi di allocazione della memoria
- [Statica](#allocazione%20statica): la memoria gestita staticamente è quella allocata dal compilatore, prima dell'esecuzione.
- Dinamica: la memoria gestita dinamicamente è quella allocata a tempo d'esecuzione. Può essere di due tipi:
	- [Pila (stack)](#allocazione%20dinamica%20mediante%20pila): oggetti allocati con politica LIFO.
	- Heap: oggetti allocati e deallocati in qualisasi momento.

### Allocazione Statica
Gli oggetti allocati staticamente risiedono in una zona fissa di memoria (stabilita dal compilatore) per tutta la durata dell'esecuazione del programma.
Solitamente sono allocati staticamente:
- Variabili globali
- Variabili locali di sottoprogrammi
- Costanti determinabili a tempo di compilazione
- Tabelle usate dal suppporto a run-time

==TODO: aggiungi foto pdf memoria statica==

### Allocazione Dinamica mediante Pila
La maggior parte dei linguaggi di programmazione moderni permette una strutturazione a blocchi dei programmi.
I blocchi, che siano in-line o associati alle procedure, vengono aperti e chiusi usando la politica LIFO: quando si entra in un blocco $A$ e poi in un blocco $B$, prima di uscire da $A$ si deve uscire da $B$.

#### Record di attivazione (RdA) per blocchi in-line 
==TODO: aggiungi foto e approfondisci==

La gestione della pila è compiuta mediante:
- sequenza di chiamata
- prologo
- epilogo
- sequenza di ritorno

L'indirizzo di un RdA non è noto a compile-time. Il puntatore RdA (o SP: Stack Pointer) punta al RdA del blocco attivo. Le informazioni contenute in un RdA sono accessibili per offset rispetto allo SP:
- indirizzo-info = contenuto(SP) + offset
- offset determinabile staticamente
- somma eseguita con unica istruzione macchina load o store
