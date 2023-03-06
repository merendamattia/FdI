# Gestione della memoria
```toc
```
--- 

Una componente importante dell'interprete di una macchina astratta è quella che si occupa della gestione della memoria. La gestione della memoria della macchina astratta di un linguaggio ad alto livello è abbastana compicata: usa varie tecniche di allocazione, sia statiche che dinamiche.

## Tipi di allocazione della memoria
- Statica
- Dinamica: può essere di due tipi:
	- Pila (stack): oggetti allocati con politica LIFO.
	- Heap: oggetti allocati e deallocati in qualisasi momento.

### Allocazione Statica
La <mark style="background: #ABF7F7A6;">memoria gestita staticamente</mark> è quella allocata dal compilatore, prima dell'esecuzione. Gli oggetti allocati staticamente risiedono in una zona fissa di memoria (stabilita dal compilatore) per tutta la durata dell'esecuazione del programma.
Solitamente sono allocati staticamente:
- Variabili globali
- Variabili locali di sottoprogrammi
- Costanti determinabili a tempo di compilazione
- Tabelle usate dal suppporto a run-time

Nel caso in cui il linguaggio non supporti la ricorsione, è possibile gestire statiscamente anche la memoria per le rimanenti componenti del linguaggio: si tratta di associare staticamente ad ogni procedura (sottoprogramma) una zona di memoria nella quale memorizzare informazioni locali della procedura stessa.
Tali informazioni sono costituite da:
- Variabili locali.
- Parametri della procedura.
- Indirizzo di ritorno.
- Eventuali valori temporanei usati.
- Informazioni di _bookkeeping_: valori di registri e info per il debugging.
![[gestione_memoria_statica.png]]

_[Torna all'indice](#gestione%20della%20memoria)_

---

### Allocazione Dinamica mediante Pila
La <mark style="background: #ABF7F7A6;">memoria gestita dinamicamente</mark> è quella allocata a tempo d'esecuzione.
La maggior parte dei linguaggi di programmazione moderni permette una strutturazione a blocchi dei programmi.
I blocchi, che siano in-line o associati alle procedure, vengono aperti e chiusi usando la politica LIFO: quando si entra in un blocco $A$ e poi in un blocco $B$, prima di uscire da $A$ si deve uscire da $B$.

![[allocazione_RdA_blocco_A.png]]
Quando entriamo nel blocco $A$, a tempo di esecuzione, dobbiamo allocare sulla pila, con un'operazione <mark style="background: #FFB86CA6;">PUSH</mark>, uno spazio per memorizzare le variabili `a` e `b`.
All'entrata del blocco $B$, dovremo allocare un nuovo spazio sulla pila per le variabili `c` e `b` (<mark style="background: #FF5582A6;">NOTA</mark>: ricordiamoci che la variabile `b` interna al blocco $B$ è diversa da quella esterna del blocco $A$). 
La situazione sopo questa seconda allocazione sarà:
```cpp
A: {
	int a = 1; 
	int b = 0;

	B: {
		int c = 3; 
		int b = 3;
	}

	b = a + 1;
}
```
All'uscita dal blocco $B$, invece, si dovrà effettuare un'operazione <mark style="background: #FFB86CA6;">POP</mark> per deallocare dalla pila lo spazio che era stato riservato per il blocco. 
Analogamente, all'uscita dal blocco $A$ dovrà essere effettuata un'altra "pop" per deallocare anche lo spazio per $A$.

_[Torna all'indice](#gestione%20della%20memoria)_

#### Record di attivazione per blocchi in-line 
La struttura di un generico <mark style="background: #ABF7F7A6;">RdA per un blocco in-line</mark> è il seguente:
![[struttura_RdA_blocco_inline.png]]

I vari settori del RdA contengono le seguenti informazioni:
1. <mark style="background: #BBFABBA6;">Risultati intermedi:</mark> nel caso in cui si debbano effettuare dei calcoli può essere necessario memorizzare alcuni risultati intermedi, anche se ad essi il programma non assegna un nome esplicito.
2. <mark style="background: #BBFABBA6;">Variabili locali:</mark> sono dichiarate all'interno di un blocco e devono avere a disposizione uno spazio di memoria la cui dimensione dipenderà dal numero e dal tipo di variabili. Queste informazioni sono note al compilatore, il quale potrà determinare la dimensione di questa parte del RdA.
	In alcuni casi vi possono essere dichiarazioni che dipendono da valori noti solo al momento dell'esecuzione: in questi casi il RdA prevede anche una parte di dimensione variabile che sarà definita al momento dell'esecuzione.
3. <mark style="background: #BBFABBA6;">Puntatore di catena dinamica:</mark> serve per memorizzare il puntatore al precedente RdA sulla pila (ossia all'ultimo RdA creato in precedenza). Questa info è necessaria perchè i RdA in genere hanno dimensioni diverse. 
	L'insieme dei collegamenti realizzari da questi puntatori è detto _catena dinamica_.

_[Torna all'indice](#gestione%20della%20memoria)_

#### Record di attivazione per le procedure 
Il caso delle procedure e delle funzioni è analogo a quello dei [blocchi in-line](#Record%20di%20attivazione%20per%20blocchi%20in-line), con qualche ulteriore complicazione dovuta al fatto che, quando si attiva una procedura, occorre memorizzare una maggiore quantità di info per gestire correttamente il controllo.

<mark style="background: #FF5582A6;">NOTA:</mark> ricordiamoci che una funzione, a differenza di una procedura, quando termina l'esecuzione restituisce un valore al chiamante.

I RdA per i due casi sono dunque uguali, ad eccezione del fatto che nel caso di una funzione, occorre tenere conto anche della locazione di memoria nella quale la funzione deve memorizzare il valore restituito.

La struttura di un generico <mark style="background: #ABF7F7A6;">RdA per una procedura</mark> è il seguente:
![[struttura_RdA_procedura.png]]

I vari settori del RdA contengono le seguenti informazioni:
1. <mark style="background: #BBFABBA6;">Risultati intermedi, variabili locali, puntatore di catena dinamica:</mark> sono gli stessi nel caso dei blocchi in-line.
2. <mark style="background: #BBFABBA6;">Puntatore di catena statica:</mark> serve per gestire le informazioni necessarie a realizzare le regole di scope statico.
3. <mark style="background: #BBFABBA6;">Indirizzo di ritorno:</mark> contiene l'indirizzo della prima istruzione da eseguire dopo che la chiamata di procedura / funzione attuale ha terminato l'esecuzione.
4. <mark style="background: #BBFABBA6;">Indirizzo del risultato:</mark> presente solo nel caso delle funzioni, contiene l'indirizzo della locazione di memoria nella quale il sottoprogramma deposita il valore restituito dalla funzione, quando quest'ultima termina. Si tratta di una locazione di memoria all'interno del RdA del chiamante.
5. <mark style="background: #BBFABBA6;">Parametri:</mark> sono memorizzati i valori dei parametri attuali usati nella chiamata della procedura / funzione.

La disposizione dei vari campi nel RdA varia a seconda delle diverse implementazioni.
Il puntatore di catena dinamica e ogni puntatore ad un RdA, punta ad una zona fissa (usualmente centrale) del RdA. Gli indirizzi dei vari campi si ottengono aggiungendo un `offset` negativo o positivo al valore del puntatore.

I nomi delle variabili normalmente non vengono memorizzati nel RdA, ma vengono gestiti direttamente dal compilatore. Inoltre, spesso i compilatori moderni ottimizzano il codice prodotto e salvano alcune informazioni nei registri inveche nel RdA.

<mark style="background: #FF5582A6;">NOTA:</mark> tutte le osservazioni che abbiamo fatto (nomi variabili, accessibilità e memorizzazione nel RdA) possono essere estese ad altre tipologie di oggetti denotabili.

_[Torna all'indice](#gestione%20della%20memoria)_

#### Gestione della pila
La seguente figura illustra la <mark style="background: #ABF7F7A6;">struttura di una pila di sistema:</mark>
![[pila_RdA.png]]

Come si nota nella figura, un puntatore esterno alla pila indica l'ultimo RdA inserito nella pila stessa (puntando ad una zona prefissata del RdA, rispetto alla quale sono calcolati gli `offset` usati per gli accessi ai nomi locali).
Questo puntatore, che noi abbiamo chiamato puntatore al RdA, è anche detto <mark style="background: #FFB86CA6;">frame pointer</mark> (o anche puntatore all'ambiente corrente). 
Nella figura è indicato anche un altro puntatore, chiamato puntatore alla pila (o <mark style="background: #FFB86CA6;">stack pointer</mark>) che indica la prima posizione di memoria libera nella pila. Lo stack pointer può anche essere omesso se il frame pointer punta sempre ad una posizione di distanza prefissata all'inizio della parte libera della pila.

I RdA vengono inseriti e rimossi dalla pila a tempo di esecuzione: quando si entra in un blocco, o si chiama una procedura, il relativo RdA verrà inserito nella pila, per poi essere eliminato dalla stessa quando si esce dal blocco o quando termina l'esecuzione della procedura.

_[Torna all'indice](#gestione%20della%20memoria)_

--- 
