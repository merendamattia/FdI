# Macchine di Turing
```toc
```
---

## L'idea di Turing
L’idea di Turing è quella di pensare ad una semplice macchina in grado di scrivere simboli su un nastro potenzialmente infinito, rappresentando il fatto (anche espresso nel [punto 7](obsidian://open?vault=Uni&file=FdI%2Ffondamenti_informatica%2F07-notazione_di_algoritmo)) che nei calcoli abbiamo solitamente a disposizione una quantità illimitata di carta dove registrare i risultati parziali del calcolo. 
L’organizzazione del nastro è fatta mediante *celle* che rappresentano la quantità di memoria unitaria. La macchina così pensata utilizzerà un *alfabeto finito*, col quale possiamo rappresentare una infinità di dati. 
Il corpo pensante della macchina (detto *controllo*) sarà realizzato mediante un automa a stati finiti deterministico (DFA). Questa restrizione modella perfettamente il [punto 8](obsidian://open?vault=Uni&file=FdI%2Ffondamenti_informatica%2F07-notazione_di_algoritmo) precedente, dove è stata assunta una complessità limitata nell’esecuzione delle istruzioni da parte della macchina. 

Tutto questo viene rappresentato matematicamente con una macchina detta *Macchina di Turing* (*MdT* in breve).

[_Torna all'indice_](#macchine%20di%20turing)

---

## Descrizione modellistica e matematica
<mark style="background: #FFB86CA6;">Una *MdT* è un dispositivo di calcolo rappresentabile con un nastro di lunghezza illimitata nel quale vengono immagazzinati i dati o sequenze di simboli del calcolo. </mark>

Uno di questi simboli è *$*: rappresenta l’assenza di simboli (spazio bianco). 
Il controllo della *MdT* ha accesso al nastro attraverso una testina di lettura e scrittura che permette di leggere o scrivere un simbolo alla volta. 

Una *MdT* è pertanto costituita da due parti: 
- il programma finito secondo cui verrà eseguito il calcolo, e
- gli organi meccanici per lo scorrimento del nastro e il comando della testina. 

La struttura a stati finiti della parte di controllo modella una macchina con una memoria che potremmo dire a breve termine, *finita*, mentre il nastro modella una memoria a lungo termine, potenzialmente *infinita*. 

> Questa distinzione tra memoria a breve e lungo termine è riscontrabile anche nelle architetture dei moderni calcolatori.

![[FdI/fondamenti_informatica/data/images/macchine_di_turing/architettura.png]]

Ad ogni istante nel calcolo, il simbolo presente nella casella esaminata dalla testina rappresenta l’input alla macchina (il simbolo $s$). 
$\to$ In risposta la macchina può decidere di modificare il simbolo e/o spostare il nastro a sinistra o a destra della casella esaminata. Questo permette di avere in input un simbolo diverso per eseguire il passo successivo della computazione (il simbolo $l_1$ se lo spostamento sarà a sinistra, $r_1$ se a destra). 
$\to$ Inoltre la testina (che si trova nello stato $q$ della memoria finita) può cambiare il suo stato scegliendolo da un insieme finito di stati possibili.

Il <mark style="background: #BBFABBA6;">comportamento di una MdT</mark> è descrivibile mediante una tabella detta <i><u>matrice funzionale</u></i> della macchina in cui le righe rappresentano gli stati del controllo mentre le colonne rappresentano i simboli di ingresso. 
In una generica cella è descritta l’azione eseguita dalla macchina nello stato corrispondente in riga e leggendo dal nastro il simbolo corrispondente in colonna.

![[matrice_funzionale.png]]

L’azione compiuta, essendo il controllo nello stato $q_i$ e leggendo il simbolo $s_j$, è in questo caso:
- portarsi in uno stato (interno) $q_r$ 
- scrivere il simbolo $s_k$
- spostare il nastro a destra $R$ o a sinistra $L$.

$\to$ Nel caso in cui $s_j = s_k$, la macchina lascia inalterato il simbolo sul nastro. 
$\to$ Se la casella corrispondente alla coppia $⟨s_j, q_i⟩$ è vuota, la macchina si ferma. 

<mark style="background: #FFF3A3A6;">Una computazione di una <i>MdT</i> sarà dunque una sequenza di passi compiuti dalla macchina.</mark>

[_Torna all'indice_](#macchine%20di%20turing)

---

### Definizione 11.1 (Macchina di Turing)
Una <i><u>Macchina di Turing M</i></u> consiste in:
1. un alfabeto finito $Σ = \{s_0, ... , s_n\}$ con almeno due simboli distinti $s_0 = \$$ (blank) e $s_1 = 0$ (tally);
2. un insieme finito di stati $Q = \{q_0, . . . , q_m\}$ tra i quali vi è lo stato iniziale $q_0$ (dunque $Q$ è non vuoto);
3. un insieme finito non vuoto di istruzioni (o quintuple) $P = \{I_1 , . . . , I_p\}$ ognuna delle quali di uno dei seguenti 2 tipi base:
	- $q\;s\;q'\;s'\;R$
	- $q\;s\;q'\;s'\;L$  
    tale che non esistono due istruzioni che iniziano con la medesima coppia $q$, $s$.

Si può dunque immaginare $P$ come la descrizione *“estensionale”* (ovvero per casi) di una funzione (in generale) parziale 
$$
δ \;:\; Q\; ×\; Σ\; →\; Q\; ×\; Σ\; ×\; \{R, L\}.
$$
Tale funzione $δ$ è detta <mark style="background: #FFB86CA6;">funzione di transizione</mark>.

> Si osservi la caratteristica *locale* delle istruzioni: il loro significato è univocamente determinato dalla parte di nastro immediatamente adiacente alla testina e dallo stato in cui la macchina si trova.

[_Torna all'indice_](#macchine%20di%20turing)

---

### Definizione 11.2 (Descrizione istantanea)
Una <i><u>descrizione istantanea (ID)</i></u> della macchina è una quadrupla
$$
⟨\;q,v,s,w\;⟩
$$
dove $v, w ∈ Σ^*$ rappresentano i caratteri significativi (cioè escludendo la sequenza illimitata di $ sempre presenti a destra e a sinistra) presenti sul nastro a sinistra e a destra della testina, $s$ è il simbolo letto dalla testina, essendo la macchina nello stato $q$.

![[descrizione_istantanea.png]]

Vediamo ora come definire formalmente il generico passo di calcolo di una MdT.

[_Torna all'indice_](#macchine%20di%20turing)

---

### Definizione 11.3 (Successore)
Definiamo una <i><u>relazione tra descrizioni istantanee</i></u>, ovvero una relazione $⊢\; ⊆ \text{ID}\; ×\; \text{ID},$ che rappresenti l’esecuzione di un singolo passo di calcolo in una data *MdT*.

l <i><u>successore ⊢</i></u> è una *“mappa”* tra descrizioni istantanee definita come:
- $⟨\;q,v,r,s w\;⟩ ⊢ ⟨\;q',v\; r',s,w\;⟩$ e $⟨\;q,v,r,ε\;⟩ ⊢ ⟨q',v\; r',\$,ε⟩$ se $q\;r\;q'\;r\;R$ è una istruzione di $P$;
- $⟨\;q,v s,r,w\;⟩ ⊢ ⟨\;q',v,s,r'\; w\;⟩$ e $⟨\;q,ε,r,w\;⟩ ⊢ ⟨\;q',ε,\$,r'w\;⟩$ se $q\;r\;q'\;r'\;L$ è una istruzione di $P$.

Una computazione sarà dunque definita come segue, ovvero come una sequenza finita di passi.

[_Torna all'indice_](#macchine%20di%20turing)

---

### Definizione 11.4 (Computazione)
Una <i><u>computazione</i></u> è una sequenza finita di ID $\alpha_0 , ... , \alpha_n$ tale che
- $\alpha_0 = ⟨\;q0,v,s,w\;⟩$ e,  
- $\alpha_i \;⊢\; \alpha_{i+1} \;\text{per ogni}\; i ∈\{\;0,...,n−1\;\}$.

Una computazione è detta terminante se esiste un $n ≥ 0$ per cui $\alpha_n = ⟨\;q, v', s', w'\;⟩$ e non vi è nessuna istruzione di $P$ iniziante con $q$ ed $s'$ (cioè $δ(q, s')$ non è definita).

[_Torna all'indice_](#macchine%20di%20turing)

---

### MdT vs Algoritmo
In accordo con il [punto 9 della precedente sezione](obsidian://open?vault=Uni&file=FdI%2Ffondamenti_informatica%2F07-notazione_di_algoritmo), esistono *MdT* che non terminano, ovvero che non calcolano nulla a partire da un dato input.

Osserviamo come una *MdT* così descritta <i><u>soddisfa i requisiti</i></u> per la definizione ragionevole di algoritmo.
1. Le istruzioni della *MdT* sono finite.  
2. La *MdT* è l’agente di calcolo che esegue l’algoritmo.  
3. Il nastro rappresenta la memoria della macchina.  
4. La *MdT* opera in modo discreto.  
5. Ad ogni *ID* corrisponde una sola azione (determinismo della *MdT*).  
6. Non esiste alcun limite all’input, essendo il nastro illimitato.  
7. La capacità della memoria (nastro) è illimitata.  
8. Le operazioni eseguibili sono semplici e quindi di complessità limitata. 
9. Non esiste alcun limite al numero di istruzioni eseguite in quanto la medesima quintupla può essere usata più volte.  
10. Possono esistere *MdT* che non calcolano nulla generando una sequenza infinita di *ID*.

[_Torna all'indice_](#macchine%20di%20turing)

---

### Teorema 11.5 (Determinismo)
$$
\text{Se} \; α ⊢ β \; \text{e} \; α ⊢ γ \; \text{con} \;α,β,γ\; ∈ \; \text{ID, allora}\; β ≡ γ.
$$

La dimostrazione è ovvia, poichè per definizione non esistono due quintuple $q\;s\;q'\;s'\;X$ aventi la medesima coppia $q, s$.

[_Torna all'indice_](#macchine%20di%20turing)

---

### Esempi
![[FdI/fondamenti_informatica/data/images/macchine_di_turing/esempi.png]]

[_Torna all'indice_](#macchine%20di%20turing)

---

## Funzioni calcolabili
Una funzione $f : \mathbb{N}^n \to \mathbb{N}$ è <mark style="background: #FFB86CA6;">Turing–calcolabile</mark> se esiste una *MdT* tale che, partendo dalla configurazione iniziale
![[definizione_11_10_1.png]]
termina nella configurazione
![[definizione_11_10_2.png]]
se $f(x_1,...,x_n)$ è definita, non termina altrimenti.
Dove per ogni $(x_1,...,x_n) ∈ \mathbb{N}^n$, $\underline{x_1} , . . . , \underline{x_n}$ , $\underline{f(x_1, . . . , x_n)}$ sono le rappresentazioni in unario rispettivamente di $x_1,...,x_n$ , $f(x1,...,xn)$ (mentre $q_f ∈ Q$ è tale per cui $δ(q_F,\$)$ è indefinito).

> Si osservi che non poniamo restrizioni sul contenuto del nastro a sinistra della testina e a destra di $f(x1, . . . , xn)$ nella configurazione finale. Invece assumiamo che a sinistra e a destra dell’input nella configurazione iniziale ci siano solo $\$$.

[_Torna all'indice_](#macchine%20di%20turing)

---

### In altre parole
Una funzione si dice <i><u>Turing-calcolabile</i></u> se esiste una *MdT* in grado di calcolare tale funzione. Questo significa che la funzione può essere espressa come una procedura algoritmica, in cui per ogni input la *MdT* produce l'output corrispondente.

La *MdT* che calcola una funzione può essere vista come un'implementazione dell'algoritmo che rappresenta la funzione stessa. L'input viene fornito alla *MdT* tramite il nastro e l'output viene prodotto anch'esso sul nastro. La computazione viene eseguita in modo deterministico, in quanto l'algoritmo e la *MdT* che lo implementa sono privi di aleatorietà.

In sostanza, una funzione è *Turing-calcolabile* se esiste un procedimento meccanico (cioè una macchina di Turing) in grado di calcolarla per qualsiasi input, senza bisogno di alcun tipo di intuizione o creatività da parte dell'operatore.

> Si osservi che, se esiste una *MdT* computante la funzione $f$, allora ne esistono infinite calcolanti la stessa funzione (si aggiungano arbitrariamente stati o simboli *"inutili"*).

[_Torna all'indice_](#macchine%20di%20turing)

---

### Esempio
![[esempio_funzioni_calcolabili.png]]

[_Torna all'indice_](#macchine%20di%20turing)

---

## MdT generalizzate
Il modello di *MdT* che abbiamo visto è solo uno dei possibili modelli matematici per definire l’effettiva calcolabilità di funzioni. È infatti possibile definire una vasta gamma di *MdT* differenti ma equivalenti rispetto alla classe di funzioni Turing-calcolabili che esse possono indurre.

Questo perchè qualunque *MdT* ottenuta anche con modifiche strutturali (per esempio aumentando il numero dei nastri o delle testine) se soddisfa le 10 condizioni che abbiamo definito per caratterizzare la [nozione intuitiva di algoritmo](obsidian://open?vault=Uni&file=FdI%2Ffondamenti_informatica%2F07-notazione_di_algoritmo), può essere simulata da una *MdT* definita come nella [Definizione 11.1 (Macchina di Turing)](#Definizione%2011.1%20(Macchina%20di%20Turing)).

> La potenza del formalismo delle *MdT* non viene dunque ridotta/aumentata modificando l’insieme dei simboli/stati o modificando la struttura stessa della macchina (numero di nastri e/o testine).

- Una *MdT* con $n$ nastri ed $m$ testine ($m ≥ n$) può essere simulata da una *MdT* con $1$ nastro ed $1$ testina.
- Una *MdT* con $n$ simboli ed $m$ stati può essere simulata da una *MdT* con $2$ stati, aumentando opportunamente il numero dei suoi simboli.
- Una *MdT* con $n$ simboli ed $m$ stati può essere simulata da una *MdT* con $2$ simboli, aumentando opportunamente il numero dei suoi stati.
- Ogni *MdT* può essere simulata da una *MdT* che può solo scrivere e non rimpiazzare simboli sul nastro.

[_Torna all'indice_](#macchine%20di%20turing)