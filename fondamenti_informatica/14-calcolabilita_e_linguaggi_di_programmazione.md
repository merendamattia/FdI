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

---

## Espressività di While e Turing completezza
È possibile rappresentare i numeri naturali in $\mathbb{D}_A$. La rappresentazione in $\mathbb{D}_A$ del numero $n$ è denotata $\underline{n}$ ed è definibile come

![[espressivita.png]]

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Funzione While-calcolabile
![[funzione_while_calcolabile.png]]

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Teorema 16.11
$$
f \;:\; \mathbb{N} → \mathbb{N} \; \text{è While-calcolabile sse è Turing-calcolabile.}
$$

> Dimostrazione di 4 pagine sul libro (pag. 147).

È possibile generalizzare quanto visto per il linguaggio While ad un arbitrario linguaggio di programmazione. Sia $\mathcal{L}$ un linguaggio di programmazione che definisce funzioni su un insieme di dati $\mathbb{D}$.

Supponiamo che esista una codifica univoca dei numeri naturali in $\mathbb{D}$, ovvero per ogni $n: \underline{n} ∈ \mathbb{D}$ e per ogni $n \ne m: \underline{n} \ne \underline{m}$. Sia $\parallel \cdot \parallel^\mathcal{L}$ la semantica del linguaggio $\mathcal{L}$ definita in modo formale:

![[teorema_16-11.png]]

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Linguaggio Turing-completo
Un linguaggio di programmazione $\mathcal{L}$ è detto *Turing-completo* se l’insieme delle funzioni $\mathcal{L}$*-calcolabili* coincide con la classe delle funzioni *Turing-calcolabili*.

Il linguaggio While è dunque Turing-completo per il [Teorema 16.11](#teorema%2016.11). In particolare, ogni linguaggio di programmazione sufficientemente espressivo per codificare i numeri naturali e comprendente i comandi di base di *assegnamento*, *composizione* ed *iterazione condizionata* tipo While è Turing-completo. Infatti, per dimostrare la Turing-completezza di un linguaggio è sufficiente dimostrare che questo è in grado di *simulare* i costrutti di base di While.

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

## For-calcolabilità e funzioni primitive ricorsive
In questa sezione presenteremo una variante al linguaggio While. 
Sostituiremo al comando While due comandi, uno di selezione ed uno iterativo molto usati in programmazione: l’*if-then-else* ed il ciclo *for*. Mostreremo ora come un linguaggio che disponga di questi due costrutti più l’assegnamento permette una espressività pari a quella del formalismo delle funzioni primitive ricorsive.

Nelle stesse ipotesi generali dei programmi While, definiamo un programma *FOR* mediante una grammatica CF nel modo seguente dove $x, y ∈ Var, \text{ e } d ∈ \mathbb{D}_A$ (in particolare, $d$ può essere $nil$):

![[for_calcolabilita.png]]

La semantica intuitiva dei due costrutti è definita nell’esercizio 16.4. Inoltre, come mostrato nell’esercizio 16.6, il costrutto if-then-else è simulabile dal for e dunque superfluo (non ne parleremo nelle dimostrazioni). Una funzione $f \;:\; \mathbb{N}^k → \mathbb{N}$ è For-calcolabile se esiste un programma FOR P tale che per ogni $x_1, \cdots , x_k ∈ \mathbb{N}$:

![[for_calcolabilita2.png]]

> Nel teorema seguente si forniranno delle definizioni più tecniche e precise, ma la sua comprensione e definizione ne può fare a meno.

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Teorema 16.14
$$
f \;:\; \mathbb{N}^m → \mathbb{N} \; \text{è FOR-calcolabile se e solo se } f \text{ è primitiva ricorsiva.}
$$

> Dimostrazione di 3 pagine sul libro (pag. 152).

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

## Interpreti e metaprogrammazione
> Per metaprogrammazione si intende la costruzione di programmi che manipolano programmi. 

Questa possibilità, sancita dalla universalità dei sistemi di calcolo Turing-completi, risiede nel fatto che i programmi possono essere codificati in modo univoco nei dati manipolati dai programmi stessi. 
La MdT universale $\mathbb{U}$ è il prototipo di metaprogramma: essa prende in input l’indice $x$ di una data MdT $M$ ed un dato $y$, e restituisce in output il risultato ottenibile attivando la macchina $M_x$ sul dato $y$:

![[metaprogramma.png]]

Traslando questo ragionamento sui linguaggi di programmazione, si ottiene il concetto di interprete. Siano $\mathcal{L}$ ed $\mathcal{S}$ due linguaggi di programmazione Turing-completi; assumiamo che operino sul medesimo insieme di dati $\mathbb{D}$.

### Definizione 16.15 (Interprete)
Un <mark style="background: #ABF7F7A6;">interprete</mark> in $\mathcal{L}$ di $\mathcal{S}$-programmi (o semplicemente di $\mathcal{S}$) è un programma $int ∈ \mathcal{L}$ tale che, per ogni $\mathcal{S}$-programma $P$, per ogni dato $d ∈ \mathbb{D}$, e per un'opportuna codifica degli $\mathcal{S}$-programmi in $\mathbb{D}$: 

![[interprete.png]]

> L’esistenza di un interprete è <u>assicurata</u> dalla Turing-completezza dei linguaggi in oggetto.

Un interprete in $\mathcal{L}$ per $\mathcal{L}$-programmi è detto <mark style="background: #BBFABBA6;">metainterprete</mark> del linguaggio $\mathcal{L}$.

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)

---

### Teorema 16.16
$$
\text{Esiste un interprete in WHILE per WHILE.}
$$

La possibilità offerta da un linguaggio Turing-completo della metaprogrammazione è alla base della esistenza di problemi algoritmicamente non risolvibili. 
<u>I limiti di ciò che è calcolabile nascono quindi dalle potenzialità del sistema di calcolo stesso.</u>
$\to$ Si può dimostrare l’indecidibilità della terminazione utilizzando il linguaggio WHILE.

![[dim_teorema_16-16.png]]

$\to$ Entrambi i casi portano ad un assurdo.

[_Torna all'indice_](#Calcolabilità%20e%20linguaggi%20di%20programmazione)