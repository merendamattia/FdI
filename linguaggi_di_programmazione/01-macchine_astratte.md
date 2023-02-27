# Macchine astratte
==TODO: indice e ritorna all'indice==
==TODO: mettere immagini al centro e non a sinistra==

# Linguaggi
==TODO: da fare==
linguaggi imperativi, dichiarativi, funzionali, logici, orientati agli oggetti

# Nozione di macchina astratta e interprete
Il termine "macchina" si riferisce alla macchina calcolatore. Una macchina astratta è un'astrazione del concetto di calcolatore fisico.  

Gli algoritmi che vogliamo eseguire devono essere rappresentati mediante le istruzioni di un opportuno linguaggio di programmazione $L$, linguaggio che sarà definito formalmente da una specifica sintassi e da una precisa semantica.

Un programma $L$ (o un programma scritto in $L$) è un insieme finito di istruzioni di $L$.

![Macchina Astratta](./images/macchina_astratta.png)

## _Definizione (Macchina Astratta)_
Supponiamo che sia dato un linguaggio di programmazione $L$. Definiamo una macchina astratta per $L$, e la indichiamo con $M_L$ , un qualsiasi insieme di strutture dati e di algoritmi che permettono di memorizzare ed eseguire programmi scritti in $L$.

Una generica macchina astratta $M_L$ è composta da una _memoria_ e da un _interprete_.
La memoria serve per immagazzinare dati e programmi, mentre l'interprete è il componente che esegue le istruzioni contenute nei programmi.

## Interprete
L'interprete dovrà compiere delle operazioni specifiche che dipendono dal particolare linguaggio $L$ che deve essere interpretato.
L'interprete esegue diversi tipi di operazioni:
1. Operazioni per l'elaborazione dei dati primitivi
2. Operazioni e strutture dati per il controllo della sequenza di esecuzione delle operazioni
3. Operazioni e strutture dati per il controllo del trasferimento dei dati
4. Operazioni e strutture dati per la gestione della memoria
==TODO: fare approfondimento==

![implementazione_interpretativa_pura](./images/implementazione_interpretativa_pura.png)

## _Definizione (Linguaggio macchina)_
Data una macchina astratta $M_L$ , il linguaggio $L$ "compreso" dall'interprete di $M_L$ è detto linguaggio macchina di $M_L$.

I programmi scritti nel linguaggio macchina di $M_L$ saranno memorizzati nelle strutture di memoria della macchina in modo tale da essere distinti dagli altri dati primitivi sui quali opera l'interprete.

![struttura_calcolatore_convenzionale](./images/struttura_calcolatore_convenzionale.png)

## L'esempio della Macchina Hardware
Come primo esempio di macchina astratta vediamo il caso di una macchina hardware: chiameremo $MH_LH$  ==(TODO da sistemare pedice)== tale macchina e $LH$ il suo linguaggio macchina.

I componenti di questa macchina astratta saranno:
- _Memoria:_ è la componente di memorizzazione della macchina fisica. È composta da vari livelli: principale, secondaria e cache.
- _Linguaggio $LH$:_ è costituito da istruzioni relativamente semplici. Ad esempio `ADD R5, R0` indica la somma del contenuto dei registri `R0` e `R5` e la memorizzazione del risultato in `R5`.
- _Interprete:_ è colui che si occupa di eseguire il ciclo `fetch-decode-execute`. ==(TODO: fare approfondimento)==

# Implementazione di un linguaggio
Una macchina astratta $M_L$ è per definizione un dispositivo che permette di eseguire programmi scritti in $L$. 
Una macchina astratta corrisponde univocamente ad un linguaggio. 
Inversamente, dato un linguaggio di programmazione $L$, vi sono molte (infinite) macchine astratte che hanno $L$ come proprio linguaggio macchina.
Tali macchine differiscono tra loro nel modo in cui l'interprete è realizzato e nelle strutture dati che utilizzano, mentre tutte coincidono nel linguaggio interpretato $L$.

## Microprogrammazione
==TODO: da approfondire==

## Realizzazione di una macchina astratta
Una qualsiasi macchina astratta $M_L$ per essere effetttivamente realizzata dovrà **prima o poi utilizzare** qualche dispositivo fisico per eseguire le istruzioni di $L$.

Possiamo realizzare una macchina astratta:
1. In HARDWARE: viene usata solo per macchine di basso livello; massima velocità, flessibilità nulla.
2. Emulazione mediante firmware: strutture dati e algoritmi realizzati da microprogrammi; alta velocità, flessibilità maggiore che hardware puro.
3. Simulazione mediante software: strutture dati e algoritmi realizzati da programmi; minore velocità, massima flessibilità, macchina ospite qualsiasi.

Nella realtà, la macchina astratta viene realizzata su di una macchina fisica mediante una combinazione delle tre tecniche sopra citate.

## Implementazione: il caso ideale
==TODO: da fare (pag13)==
### Implementazione interpretativa pura
==TODO: da fare (pag14)==
![implementazione_interpretativa_pura](./images/implementazione_interpretativa_pura.png)
### Implementazione compilativa pura
==TODO: da fare (pag15)==
### Confronto tra le due tecniche
==TODO: da fare (pag16)==
