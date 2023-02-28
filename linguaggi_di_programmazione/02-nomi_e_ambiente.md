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

Per _aliasing_ si intende quella situazione in cui uno stesso oggetto è visibile mediante nomi diversi nello stesso ambiente. È molto rischioso. 
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

## Tipi d'ambiente
L'ambiente associato ad un blocco è costituito dalle tre parti seguenti:
- _Locale:_ è costituito dall'insieme delle associazioni per nomi dichiarati localmente al blocco (variabili locali e parametri formali);
- _Non locale:_ è costituito dalle associazioni relative ai nomi che sono visibili all'interno di un blocco ma che non sono stati dichiarati localmente;
- _Globale:_ è costituito dalle associazioni create all'inizio dell'esecuzione del programma principale.

==(TODO: aggiungere codice pagina 151 con relativi commenti)

## Operazioni sull'ambiente
- _Creazione_ di un'associazione fra nome ed oggetto denoatto (naming): dichiarazione locale in blocco;
- _Riferimento_ di un oggetto denotato mediante il suo nome (referencing): corrisponde all'uso di un nome;
- _Disattivazione_ di un'associazione fra il nome e l'oggetto denotato: corrisponde all'ingresso in un blocco dove viene creata localmente una nuova associazione per quel nome;
- _Riattivazione_ di un'associazione fra il nome e l'oggetto denotato: avviene quando si esce da un blocco dove era stata creata localmente una nuova associazione per quel nome;
- _Distruzione_ di un'associazione fra il nome e l'oggetto denotato (unnaming): viene effettuata quando si esce dal blocco dove tali associazioni erano state create.

## Operazioni su oggetti denotabili
- Creazione
- Accesso
- Modifica
- Distruzione
- ==(TODO: da approfondire pag153)==

## Tempo di vita 
La vita di un oggetto non coincide conn la vita dei legami per quell'oggetto.
La vita dell'oggetto è più lunga di quella del legame
==(TODO: da approfondire pag153)==

# Regole di scope
Sono le regole che, in ogni linguaggio, determinano la visibilità dei nomi.
Esistono due tipologie di _scoping:_
- Scope statico
- Scope dinamico

## Scope statico
Lo scope statico richiede che il riferimento a un nome non locale e non globale venga risolto utilizzando il legame testualmente più vicino, procedendo dall'interno verso l'esterno.  

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
        C: { int c = 3;
            int d;
            d = a + b + c;
            write(d);        //stampa 6
        }
        D: {int e;
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
==TODO: aggiungi da foto==