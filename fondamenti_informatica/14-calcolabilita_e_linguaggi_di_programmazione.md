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