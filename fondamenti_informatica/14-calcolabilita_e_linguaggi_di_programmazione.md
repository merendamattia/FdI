# Calcolabilità e linguaggi di programmazione
```toc
```
---

## Linguaggio While
*While* è un linguaggio ad alto livello adeguato per rappresentare tutte le funzioni calcolabili che permette di manipolare semplici strutture dati.

> Al fine di evitare l’aritmetizzare dei programmi, in questo capitolo studieremo un semplice linguaggio di programmazione imperativo chiamato While in grado di manipolare strutture dati più complesse.

> Aritmetizzare un programma significa rappresentare il programma come una formula matematica che può essere manipolata e analizzata utilizzando le tecniche della teoria degli insiemi, dell'aritmetica e della logica matematica.

$\to$ Il linguaggio While è un linguaggio ad alto livello *Turing-equivalente*.
$\to$ Permette di manipolare semplici strutture dati simili a quelle impiegate in *Scheme* e *Lisp*.
$\to$ Questa possibilità consente di evitare l'aritmetizzazione: si potranno quindi considerare direttamente i programmi come i dati.
$\to$ Questo è il passo fondamentale per definire il concetto di funzione universale.

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

## Strutture dati di While
<mark style="background: #FFB86CA6;">Le strutture dati del linguaggio *While* sono alberi binari.</mark> Questi permettono di rappresentare la sintassi concreta dei programmi come dati. 
Sia $A$ un insieme finito di atomi, o espressioni elementari, e $nil$ l’albero vuoto. 
L’insieme degli alberi $\mathbb{D}_A$ è definito ricorsivamente come il più piccolo insieme tale che:

![[insieme_degli_alberi.png]]

In altri termini, se $A = \{a_1 , \cdots , a_n \}$, $\mathbb{D}_A$ è il linguaggio generato dalla grammatica CF: $\mathbb{D}_A \to nil \;| \;a_1 \;|\; \cdots \;| \; a_n \; | \;(D_A \cdot D_A)$.

Esempio:
![[FdI/fondamenti_informatica/data/images/calcolabilita_e_linguaggi_di_programmazione/esempio1.png]]

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Teorema 16.1
$$
\mathbb{D}_A \text{ è isomorfo a } \mathbb{N}
$$
![[dim_teorema-16-1.png]]

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

## Sintassi di While
$\to$ Sia $Var$ un insieme finito e numerabile di variabili e sia $x$ una generica variabile.
$\to$ Sia $d$ un generico elemento di $\mathbb{D}_A$.

La sintassi di While è definita dalla seguente grammatica in forma BNF:
![[sintassi_while.png]]

Assumiamo inoltre che in `Listavar` le variabili siano tutte distinte. 

> Si osservi come in questo linguaggio non vi sia la dichiarazione di tipo per le variabili. Tutte le variabili infatti possono assumere solo valori di *"tipo"* $\mathbb{D}_A$.

Esempio:
![[esempio_16-2.png]]

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

## Semantica di While
$\to$ La semantica di un programma While è data in termini di un sistema di transizione. 
$\to$ Per definirla, dobbiamo prima definire il concetto di stato. 
$\to$ Questo rappresenta la memoria della macchina preposta all’esecuzione di programmi While. 
$\to$ La memoria può essere vista come un nastro in cui ogni cella corrisponde esattamente ad una variabile in $Var$ e può contenere esclusivamente valori in $\mathbb{D}_A$. 
$\to$ Uno stato $\sigma$ è rappresentabile come una funzione parzialmente definita da variabili in valori $\sigma : Var → \{\mathbb{D}_A \; \cup \perp \}$. L’insieme di tutti gli stati è detto State. 
$\to$ Se $\sigma ∈ \text{State}$, allora il valore dello stato (memoria) $\sigma$ in corrispondenza alla variabile $x ∈ Var$ è dato dal valore della funzione $\sigma$ in $x$, ovvero $\sigma(x) ∈ \mathbb{D}_A$. 
$\to$ Un comando ha lo scopo di modificare lo stato corrente.

> Il simbolo $\perp$ indica il valore indefinito.
> Inoltre, per semplicità, assumeremo che le variabili abbiano sempre il valore iniziale $nil$.

La <mark style="background: #BBFABBA6;">semantica intuitiva</mark> dei comandi di While è data nel seguente modo:

![[semantica_intuitiva.png]]

Possiamo quindi dare la semantica formale di While induttivamente sulla sintassi come sistema di transizione:
- [Semantica delle espressioni](#Semantica%20delle%20espressioni)
- [Semantica dei comandi](#Semantica%20dei%20comandi)
- [Semantica dei Programmi](#Semantica%20dei%20Programmi)

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Semantica delle espressioni
Ogni espressione rappresenta un albero. Al fine di valutare espressioni contenenti variabili è necessario per la loro valutazione ricorrere alla memoria. La semantica delle espressioni è data dunque da una funzione di interpretazione semantica:
$$
\xi \; :\; Exp\;  × \; State \to \mathbb{D}_A
$$
definita come nella seguente tabella:

![[semantica_delle_espressioni.png]]

> Il risultato dell’espressione $E_1 = E_2$ può essere `false` oppure `true`; queste entità sintattiche possono essere usate liberamente come abbreviazioni degli alberi $nil$ e $(nil.nil)$, rispettivamente.

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Semantica dei comandi
La semantica dei comandi è definita induttivamente sulla sintassi dal sistema di transizione della seguente tabella: 

![[semantica_dei_comandi.png]]

Le *configurazioni* del sistema di transizione sono definite da coppie: $Com\; ×\; State$. Ogni configurazione $⟨C,σ⟩$ rappresenta il comando $C$ da eseguire e lo stato $σ$ in cui questo viene eseguito.

È necessario rappresentare il caso in cui un comando sia stato completamente eseguito. A questo scopo:
- si rappresenta il comando vuoto con $\epsilon$ (il simbolo della stringa vuota);
- per essere rigorosi si stabilisce che le configurazioni sono in realtà coppie di $(Com\; \cup \; \{\epsilon\}) ×\; State$;
- ma per semplicità notazionale, si scrive $σ$ invece di $⟨ε,σ⟩$.

Aggiornamento dello stato:
![[aggiornamento_dello_stato.png]]

> Queste proprietà definiscono le memorie *"non rotte"*.
> $\to$ La memoria si comporta da memoria.

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Semantica dei Programmi
La semantica di un programma While è definita a partire dalla semantica dei comandi, o meglio dalla chiusura transitiva $\to ^*$ della relazione di transizione dei comandi.
Questa è codificabile come funzione totale, introducendo il simbolo speciale $\uparrow$ nel codominio:
$$
\parallel\cdot\parallel^W \;:\; Prog \to (\mathbb{D}_A^n \;\to\; \mathbb{D}_A^n \; ∪ \;\{\uparrow\})
$$

La semantica $\parallel P \parallel^W$ di un programma 
$$
P = read(x_1,..., x_n);\; C;\; write(y_1,...,y_m) 
$$
è definita come segue, per ogni $d_1, \cdots, d_n ∈ \mathbb{D}_A:$

![[semantica_dei_programmi.png]]

Esempio:
![[esempio_semantica_programmi.jpeg]]

> Esercizio stile esame:
> ![[esercizio_stile_esame.png]]

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)