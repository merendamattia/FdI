# I nomi e l'ambiente
1. [Nomi e oggetti](#nomi%20e%20oggetti%20denotabili)
2. [Ambiente](#ambiente)
	- [Blocchi](#blocchi)
	- [Tipi d'ambiente](#tipi%20d'ambiente)
	- [Operazioni sull'ambiente](#operazioni%20sull'ambiente)
	- [Operazioni su oggetti denotabili](#operazioni%20su%20oggetti%20denotabili)
	- [Tempo di vita](#tempo%20di%20vita)
3. [Regole di scope](#regole%20di%20scope)
	- [Scope statico](#scope%20statico)
	- [Scope dinamico](#scope%20dinamico)

# Nomi e oggetti denotabili
Un **nome** è una sequenza di caratteri alfanumerici ed è associato ad un oggetto *denotabile*. Nella maggior parte dei linguaggi i nomi sono costituiti da *identificatori*, ossia da token alfanumerici.

Gli oggetti ai quali può essere dato un nome si dicono _oggetti denotabili_. Ne esistono due tipologie:
- Nomi definiti dall'utente: variabili, parametri formali, procedure (in senso lato), tipi definiti dall'utente, etichette, moduli, costanti definite dall'utente, eccezioni;
- Nomi definiti dal linguaggio di programmazione: tipi primitivi, operazioni primitive, costanti predefinite.

Si parla di *binding* quando viene stabilita un'associazione tra il nome e l'oggetto. 

_[Torna all'indice](#i%20nomi%20e%20l'ambiente)_

---

# Ambiente
Definiamo **ambiente** (*referencing environment*) l'insieme delle associazioni fra nomi e oggetti denotabili esistenti a run-time in uno specifico punto del programma ed in uno specificco momento dell'esecuzione (quest'ultimo conta solo se il linguaggio non è staticamente compilato).

Una **dichiarazione** (esplicita o implicita) è un costrutto che introduce un'associazione; chiaramente più nomi possono riferirsi allo stesso oggetto (*aliasing*):

```c
int x; // dichiarazione di una variabile

int func() { // definizione (e dichiarazione) di una funzione
	return 0;
}

typedef T = int; // dichiarazione di un nuovo tipo T, che coincide col tipo int

x = 3;
int& a = x; // a si riferisce a x
int& b = x; // b si riferisce a x
```

## Blocchi
L'ambiente è strutturato attraverso l'utilizzo di **blocchi**: una regione testuale del programma, identificata da un segnale di inizio ed uno di fine, che può contenere dichiarazioni _locali_ a quella regione.
Nei linguaggi moderni l'ambiente è _strutturato_.
- `begin ... end` -> Algol, Pascal
- `{ ... }` -> C, Java
- `( ... )` -> Lisp
- `let ... in .. end` -> ML

I blocchi possono essere:
- associati ad una procedura
	testualmente corrisponde al corpo della procedura stessa, esteso con le dichiarazioni dei parametri formali;
``` cpp
void foo() {
	...
}
```
- anonimi (o *in-line*)
	non corrisponde ad una dichiarazione di procedura e può dunque comparire, in genere, in qualsiasi punto del programma.
- annidati
	ad esempio un blocco in-line dentro una definizione di procedura.
``` c++
int main() {
	int x = 5;
	{ // blocco annidato dentro la funzione main
		int x = 1;
		std::cout << x << std::endl; // stampa 1
	}
	std::cout << x << std::endl; // stampa 5
}
```

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
```

_[Torna all'indice](#i%20nomi%20e%20l'ambiente)_

## Tipi d'ambiente
L'ambiente associato ad un blocco è costituito dalle tre parti seguenti:
- **Locale**
	costituito dall'insieme delle associazioni per nomi dichiarati localmente al blocco (variabili locali e parametri formali);
- **Non locale** 
	costituito dalle associazioni ereditate da altri blocchi;
``` cpp
int x = 5;
{
	x++; // associazione con x ereditata
}
```
- **Globale**
	comprende le associazioni che sono comuni a tutti i blocchi. 

> Non tutti i linguaggi di programmazione hanno un ambiente globale.

## Operazioni sull'ambiente
- _Creazione_ di un'associazione fra nome ed oggetto denotato (naming): dichiarazione locale in blocco;
- _Riferimento_ di un oggetto denotato mediante il suo nome (referencing): corrisponde all'uso di un nome;
- _Disattivazione_ di un'associazione fra il nome e l'oggetto denotato: corrisponde all'ingresso in un blocco dove viene creata localmente una nuova associazione per quel nome;
- _Riattivazione_ di un'associazione fra il nome e l'oggetto denotato: avviene quando si esce da un blocco dove era stata creata localmente una nuova associazione per quel nome;
- _Distruzione_ di un'associazione fra il nome e l'oggetto denotato (unnaming): viene effettuata quando si esce dal blocco dove tali associazioni erano state create.

_[Torna all'indice](#i%20nomi%20e%20l'ambiente)_

## Operazioni su oggetti denotabili
- *Creazione*
- *Accesso*
- *Modifica* (se l'oggetto è modificabile)
- *Distruzione*

L'ordine in cui dovrebbero avvenire le operazioni:
1. Creazione di un oggetto
2. Creazione di un legame per oggetto
3. Riferimento all'oggetto, tramite il legame
4. Disattivazione di un legame (cambio di blocco)
5. Riattivazione di un legame
6. Distruzione di un legame
7. Distruzione di un oggetto


### Tempo di vita 
Il tempo che intercorre tra la creazione e la distruzione di un oggetto viene detto *lifetime* (1-7); quello che intercorre tra la creazione del legame e la sua distruzione è la *vita dell'associazione* (2-6).

Un oggetto denotabile può avere un tempo di vita maggiore di quello dell'associazione fra nome e l'oggetto stesso, come nel caso in cui si passi per riferimento una variabile ad una procedura.

Può anche accadere che il tempo di vita di un'associazione fra nome e oggetto denotato sia superiore a quello dell'oggetto stesso. Più precisamente, può avvenire che un nome permetta di accedere ad un oggetto che non esiste più :
``` cpp
int* pi = new int; // creazione di un oggetto
int& x = *pi; // creazione di un legame

delete pi; // L'oggetto non c'è più ma il legame tramite x si
x = 7; // utlizzo del legame -> Undefined behaviour
```

_[Torna all'indice](#i%20nomi%20e%20l'ambiente)_

---

# Regole di scope
Sono le regole che, in ogni linguaggio, determinano la visibilità dei nomi. Esistono due tipologie di _scoping:_
- Scope statico
- Scope dinamico

## Scope statico
Lo **scope statico** richiede che il riferimento a un nome non locale e non globale venga risolto utilizzando il legame testualmente più vicino, procedendo dall'interno verso l'esterno.  

Per risolvere un riferimento a un nome si esamina il blocco locale e tutti quelli via via più esterni che staticamente lo includono fino ad individuarne il legame.  

La determinazione degli scope può essere effettuata dal compilatore, scegliendo il più recente legame elaborato a tempo di compilazione.  
Generalmente i linguaggi compilati usano lo scope statico.  
```cpp
// Esempio di scope statico
A: { 
	int a = 1;
    B: { 
	    int b = 2;
        int c = 2;
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

_[Torna all'indice](#i%20nomi%20e%20l'ambiente)_

## Scope dinamico
Secondo la regola dello **scope dinamico**, l'associazione valida per un nome $X$, in un qualsiasi punto $P$ di un programma, è la più recente (in senso temporale) associazione creata per $X$ che sia ancora attiva quando il flusso di esecuzione arriva a $P$.  

In poche parole lo scope dinamico richiede la scelta del più recente legame ancora attivo stabilito a tempo di esecuzione.
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
        write(x);        //stampa 4, con lo scope statico avrebbe stampato 0
    }
    write(x);            //stampa 5
}
```

_[Torna all'indice](#i%20nomi%20e%20l'ambiente)_

## Scope statico vs scope dinamico

Riassumendo

| Scope statico (*statically scoped*)| Scope dinamico (*dynamically scoped*)|
| ------------- | -------------- |
| L'informazione completa deriva dal testo del programma | L'informazione deriva dall'esecuzione del programma |
| Le associazioni sono note a tempo di compolazione | Spesso è la causa di programmi meno "leggibili" |
| Valgono i principi di indipendenza | Non valgono i principi di indipendenza |
| È complesso da implementare, ma è più efficente | È semplice da implementare, però è poco efficiente |
| Alcuni esempi di linguaggi che lo utilizzano sono Algo, Pascal, C, Java | Alcuni esempi di linguaggi che lo utilizzano sono Lisp, Perl |

Questi differiscono solo in presenza congiunta di:
- Ambiente non locale e non globale
- Presenza di proecdure

Differiscono solo in presenza congiunta di un ambiente non locale e non globale.

_[Torna all'indice](#i%20nomi%20e%20l'ambiente)_
