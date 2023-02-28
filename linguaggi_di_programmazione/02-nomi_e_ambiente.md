# I nomi e l'ambiente
==TODO: indice e ritorna all'indice==

# Nomi e oggetti denotabili
Un nome è una sequenza di caratteri usata per rappresentare, o denotare, un altro oggetto.
Nella maggior parte dei linguaggi i nomi sono costituiti da identificatori, ossia da token alfanumerici.

Gli oggetti ai quali può essere dato un nome si dicono _oggetti denotabili_. Esistono due tipi di oggetti denotabili:
- Nomi definiti dall'utente: variabili, parametri formali, procedure (in senso lato), tipi definiti dall'utente, etuchette, moduli, costanti definite dall'utente, eccezioni;
- Nomi definiti dal linguaggio di programmazione: tipi primitivi, operazioni primitive, costanti predefinite.

Il legame o associazione (binding) è l'associazione che c'è tra un nome e l'oggetto.

# Ambiente
Un _ambiente_ (referencing environment) è l'insieme delle associazioni fra nomi e oggetti denotabili esistenti a run-time in uno specifico punto del programma ed in uno specificco momento dell'esecuzione.

Una _dichiarazione_ è un costrutto che permette di introdurre un'associazione nell'ambiente.
```c
int x; // dichiarazione di una variabile

int func (){ // dichiarazione di una funzione
	return 0;
}

type T = int; // dichiarazione di un nuovo tipo T, che coincide col tipo int
```

Lo stesso nome può denotare oggetti distinti in punti diversi del programma.

Nei linguaggi moderni l'ambiente è strutturato (diviso in blocchi)

## Dichiarazione
La _dichiarazione_ è un meccanismo con il quale si introduce un associazione in un ambiente.
Le dichiarazioni possono essere di due tipi:
- _impliciti_, presente ad esempio in python
- _espliciti_, presente ad esempio in c

Per _aliasing_ si intende quella situazione in cui uno stesso oggetto è visibile mediante nomi diversi nello stesso ambiente. È molto rischioso, perché è insidioso. 
Il passaggio per riferimento è una possibile causa di aliasing.

## Blocchi
Un _blocco_ è una regione testuale del programma, identificata da un segnale di inizio ed uno di fine, che può contenere dichiarazioni _locali_ a quella regione.
Nei linguaggi moderni l'ambiente è _strutturato_.
- `begin ... end` -> Algol, Pascal
- `{ ... }` -> C, Java
- `( ... )` -> Lisp
- `let ... in .. end` -> ML

I blocchi possono essere:
- _anonimi_ (o in-line):  
- associati ad una procedura: 
==TODO: da approfondire==

### Perchè i blocchi?
I blocchi hanno anche la funzione di "raggruppare" una serie di comandi in un'entità sintattica che possa essere considerata come un unico comando (composto).

Una _dichiarazione locale_ ad un blocco è visibile in quel blocco e in tutti i blocchi in esso annidati, a meno che non intervenga in tali blocchi una nuova dichiarazione dello stesso nome. In tal caso, nel blocco in cui compare la ridefinizione, la nuova dichiarazione _nasconde_ (o maschera) la precedente.

```cpp
int x = 1;
{
	int x = 3;
	write(x); //viene stampato 3
}
write(x); //viene stampato 1
...
```

L'utilizzo dei blocchi permette un ottimizzazione del codice, perché le variabili allocate all'inizio del blocco e deallocate al termine di quest'ultimo, migliorando la memoria utilizzata.

```cpp
int x = 1;
int y = 2;
{
	int tmp = x; //tmp viene allocata
	x = y;
	y = tmp;
	//tmp viene deallocata
}
...
```


## Tipi d'ambiente
L'ambiente associato ad un blocco è costituito dalle tre parti seguenti:
- _Locale:_ è costituito dall'insieme delle associazioni per nomi dichiarati localmente al blocco (variabili locali e parametri formali);
- _Non locale:_ è costituito dalle associazioni relative ai nomi che sono visibili all'interno di un blocco ma che non sono stati dichiarati localmente;
- _Globale:_ è costituito dalle associazioni, comuni a tutti i blocchi, create all'inizio dell'esecuzione del programma principale (dichiarazioni esplicite di variabili globali, dichiarazioni del bloccho più esterno, associazioni esportate da moduli)

```cpp
A: { 
	int a = 1;
    B: { 
	int b = 2;
        int c=2;
        C: {
	    int c = 3;
            int d;
            d = a + b + c;
            write(d);        //stampa 6
        }
        D: {
	    int e;
            e = a + b + c;
            write(e);        //stampa 5
        }
    }
}
```
## Operazioni sull'ambiente
- _Creazione_ di un'associazione fra nome ed oggetto denoatto (naming): dichiarazione locale in blocco;
- _Riferimento_ di un oggetto denotato mediante il suo nome (referencing): corrisponde all'uso di un nome;
- _Disattivazione_ di un'associazione fra il nome e l'oggetto denotato: corrisponde all'ingresso in un blocco dove viene creata localmente una nuova associazione per quel nome;
- _Riattivazione_ di un'associazione fra il nome e l'oggetto denotato: avviene quando si esce da un blocco dove era stata creata localmente una nuova associazione per quel nome;
- _Distruzione_ di un'associazione fra il nome e l'oggetto denotato (unnaming): viene effettuata quando si esce dal blocco dove tali associazioni erano state create.

## Operazioni su oggetti denotabili e tempo di vita
- Creazione
- Accesso
- Modifica
- Distruzione

L'ordine in cui dovrebbero avvenire gli eventi:
1. Creazione di un oggetto
2. Creazione di un legame per oggetto
3. Riferimento all'oggetto, tramite il legame
4. Disattivazione di un legame (cambio di blocco)
5. Riattivazione di un leagme
6. Distruzione di un legame
7. Distruzione di un oggetto

Il tempo tra 1 e 7 corrisponde al _lifetime_ dell'oggetto, il tempo tra 2 e 6 corrisponde alla vita dell'associazione. Quindi il tempo di vita di un oggetto non conincide con la vite dei legami per quell'oggetto, la sua vita deve essere più lunga di quella del legame.

Purtroppo l'ordine sopra elencato non viene sempre rispettato, presentando la vita dell'oggetto più breve di quella del legame, causando così un _undefined behavior_

```cpp
int *pi = new int; // creazione di un oggetto
int &x = *pi; // creazione di un legame

delete pi; // distruzione dell'oggetto
x = 7; // utlizzo del legame -> undefined behavior
```

- ==(TODO: da approfondire pag153)==


# Regole di scope

Sono le regole che, in ogni linguaggio, determinano la visibilità dei nomi.

Esistono due tipologie di _scoping:_
- Scope statico
- Scope dinamico

## Scope statico
Lo scope statico (o lessicale) richiede che il riferimento a un nome non locale e non globale venga risolto (sintatticamente) utilizzando il legame testualmente più vicino, procedendo dall'interno verso l'esterno. 

Per risolvere un riferimento a un nome si esamina il blocco locale e tutti quelli via via più esterni che staticamente lo includono fino ad individuarne il legame.  

La determinazione degli scope può essere effettuata dal compilatore, scegliendo il più recente legame attivo elaborato a tempo di compilazione.  
Generalmente i linguaggi compilati usano lo scope statico.

```cpp
// Esempio di scope statico
A: { 
	int a = 1;
    B: { 
	int b = 2;
        int c=2;
        C: {
	    int c = 3;
            int d;
            d = a + b + c;
            write(d);        //stampa 6
        }
        D: {
	    int e;
            e = a + b + c;
            write(e);        //stampa 5
        }
    }
}
```

Vantaggi: avere il codice indipendente dalla posizione.

## Scope dinamico
Secondo la regola dello scope dinamico, l'associazione valida per un nome $X$, in un qualsiasi punto $P$ di un programma, è la più recente (in senso temporale) associazione creata per $X$ che sia ancora attiva quando il flusso di esecuzione arriva a $P$.  

In poche parole lo _scope dinamico_ richiede la scelta del più recente legame ancora attivo stabilito a tempo di esecuzione.
```cpp
// Esempio di scope dinamico
{
    int x = 0;
    void p(int n) {
        x = n + 1;
    }
    p(3); 
    write(x);            //stampa 4
    {
        int x = 0;
        p(4);
        write(x);        //stampa 0
    }
    write(x);            //stampa 5
}
```

## Scope statico vs scope dinamico

Riassumendo

| Scope statico | Scope dinamico |
| ------------- | -------------- |
| L'informazione completa deriva dal testo del programma | L'informazione deriva dall'esecuzione del programma |
| Le associazioni sono note a tempo di compolazione | Spesso è la causa di programmi meno "leggibili" |
| Valgono i principi di indipendenza | Non valgono i principi di indipendenza |
| È complesso da implementare, ma è più efficente | È semplice da implementare, però è poco efficiente |
| Alcuni esempi di linguaggi che lo utilizzano sono Algo, Pascal, C, Java | Alcuni esempi di linguaggi che lo utilizzano sono Lisp, Perl |

Questi differiscono solo in presenza congiunta di:
- Ambiente non locale e non globale
- Presenza di proecdure


== aggiungi da foto==


## Determinazione dell'ambiente

L'ambiente è determinato da:
- regole di scope, statico o dinamico
- regole specifiche
