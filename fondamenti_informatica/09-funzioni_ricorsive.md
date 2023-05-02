# Funzioni ricorsive

```toc
```
---

## Funzioni primitive ricorsive

L’insieme dei numeri naturali è facilmente caratterizzabile mediante induzione, ovvero affermando che ogni numero naturale $n$ è esprimibile come una iterazione della operazione elementare di *successore* applicata al valore costante $0:\; n = S^n(0)$. 
Pertanto
$$
\mathbb{N} = \{0,\; S(0),\; S(S(0)),\; S(S(S(0))), \; \dots \}
$$

> Nel seguito indicheremo spesso $S(x)$ con $x+1$.

Questo procedimento induttivo per definire i numeri naturali si basa sull’idea che ogni numero naturale è definibile a partire da un numero più semplice (in questo caso minore nell’ordinamento usuale sui naturali) applicando l’operazione di successore.

Una <mark style="background: #FFB86CA6;">definizione ricorsiva di funzione</mark> è una definizione dove il valore della funzione per un dato argomento è direttamente correlato al valore della medesima funzione su argomenti "più semplici" o al valore di funzioni "più semplici".

Trattando i naturali, consideriamo dunque la costante $0$ come <mark style="background: #ABF7F7A6;">funzione costante elementare</mark>. Supponiamo inoltre di avere a disposizione come funzione elementare l’operazione di <mark style="background: #ABF7F7A6;">successore</mark>, che ci permette di definire qualsiasi numero naturale, e la <mark style="background: #ABF7F7A6;">funzione identica</mark>. 
Queste assunzioni ci portano a definire il concetto di *funzione ricorsiva di base*.

[_Torna all'indice_](#Funzioni%20ricorsive)

---

### Funzioni ricorsive di base
Si dicono funzioni ricorsive di base le seguenti funzioni:
- La funzione *costante* $0: λx \; . \; 0\;$
- La funzione *successore* $S: λx \; . \; x + 1$
- La funzione *identità*, o $i$-esima proiezione, $π_i : λx_1 \cdots x_n \;. \;x_i \;\;\text{con}\;\; 1 ≤ i ≤ n$

[_Torna all'indice_](#Funzioni%20ricorsive)

---

### Meccanismo di definizione
![[definizione_composizione_ricorsione_primitiva.png]]

Tutte e sole le funzioni definibili a partire dalle precedenti funzioni ricorsive di base mediante composizione e ricorsione primitiva definiscono l’insieme delle funzioni *primitive ricorsive*.

> L’idea è quella di costruire via via funzioni effettivamente calcolabili a partire dalle funzioni (banalmente) effettivamente calcolabili di base, ovvero $0$ e $S$, costruendo da queste, per composizione e ricorsione primitiva, funzioni via via più complesse.

[_Torna all'indice_](#Funzioni%20ricorsive)

---

### Classe P
La classe $\mathcal{P}$ delle funzioni *primitive ricorsive* è la più piccola classe (ovvero l’intersezione di tutte le classi) di funzioni contenenti le funzioni ricorsive di base e chiuse per composizione e ricorsione primitiva.

> Segue direttamente dalla definizione che, per ogni funzione $f, f ∈ \mathcal{P}$ sse esiste una sequenza finita di funzioni $f_1,...,f_n \;$, tale che: $f_n = f$ e per ogni funzione $f_j \;$, con $j ≤ n$, o $f_j$ è una funzione ricorsiva di base, oppure è ottenuta mediante composizione o ricorsione primitiva a partire da funzioni $f_{i_1}\;, . . . , f_{i_k} \;$ con $i_1, . . . , i_k < j$ e per le quali vale la stessa proprietà. 
> Queste non sono altro che le condizioni per fissare un sistema formale.

[_Torna all'indice_](#Funzioni%20ricorsive)

---

### Esempi

![[FdI/fondamenti_informatica/data/images/funzioni_ricorsive/esempi.png]]

[_Torna all'indice_](#Funzioni%20ricorsive)

---

### Teorema 12.8
$$
\textit{Le funzioni primitive ricorsive sono totali.}
$$

Le <mark style="background: #FFB8EBA6;">funzioni primitive ricorsive sono totali</mark> perché sono definite in modo ricorsivo a partire da alcune funzioni base (o primitive) che sono totali, come ad esempio la funzione successore $S(x) = x+1$ e le proiezioni $π(x_1, \ldots, x_n) = x_i$. 
Ogni funzione primitiva ricorsiva è ottenuta componendo un numero finito di volte queste funzioni base, mediante l'uso di operazioni come la composizione, la ricorsione primitiva e la somma.

Inoltre, è importante notare che tutte le operazioni coinvolte nella definizione delle funzioni primitive ricorsive (composizione, ricorsione primitiva, somma, prodotto) sono operazioni totali. Ciò significa che, se le funzioni di partenza sono totali, allora la funzione ottenuta attraverso la loro composizione e l'uso di queste operazioni sarà anch'essa totale.

> In altre parole, le funzioni primitive ricorsive sono definite in modo tale che per ogni input possibile, l'algoritmo che le calcola termina sempre restituendo un output corretto. Ciò garantisce che queste funzioni siano totali e quindi ben definite per ogni possibile input.

[_Torna all'indice_](#Funzioni%20ricorsive)

---

## Funzioni parziali ricorsive
### Definizione 12.10
Sia $f$ una funzione <u>totale</u> $n + 1$ aria, allora definiamo la funzione
![[definizione_12_10.png]]
Tale operatore tra funzioni è detto μ-operatore ed una funzione così definita è detta definita per *minimizzazione* o μ-ricorsione da $f$.

> Chiaramente una funzione definita per minimizzazione è in generale, per definizione, parziale.

[_Torna all'indice_](#Funzioni%20ricorsive)

### In altre parole
Una <mark style="background: #FFB86CA6;">funzione definita per minimizzazione</mark> è una funzione parziale ricorsiva che viene definita utilizzando l'operazione di minimalizzazione. L'idea alla base della minimalizzazione è quella di trovare il valore minimo che fa sì che una determinata condizione sia soddisfatta.

Formalmente, data una funzione f(x,y) definita su una coppia di valori x e y, la funzione di minimalizzazione h(x) cerca il valore minimo di y tale che f(x,y) è definita, ovvero esiste un valore y per il quale f(x,y) restituisce un risultato. Se non esiste alcun valore y per cui f(x,y) sia definita, allora h(x) non restituisce alcun valore.

La funzione di minimalizzazione può essere definita utilizzando il costruttore di minimalizzazione delle funzioni parziali ricorsive. Questa costruzione è molto potente perché consente di definire funzioni che non possono essere definite utilizzando solo la composizione e la ricorsione primitiva.

[_Torna all'indice_](#Funzioni%20ricorsive)

---

### Definizione 12.12
La classe delle funzioni parziali ricorsive è la minima classe $\mathcal{PR}$ di funzioni contenente $\mathcal{P}$ e chiusa per μ-ricorsione.

Esempio:
![[esempio.png]]

[_Torna all'indice_](#Funzioni%20ricorsive)

---

## Equivalenza tra MdT e funzioni parziali ricorsive
$$
f : \mathbb{N} \to \mathbb{N} \;\text{è parziale ricorsiva se e solo se è Turing calcolabile.}
$$
> Dimostrazione di 5 pagine sul libro (pag. 118).

Le MdT e le funzioni parziali ricorsive (FPR) sono due modelli computazionali equivalenti. Ciò significa che ogni funzione parziale ricorsiva può essere calcolata da una MdT, e viceversa, ogni MdT può essere rappresentata come una funzione parziale ricorsiva.

La corrispondenza tra le MdT e le FPR si basa sul fatto che entrambi i modelli computazionali sono in grado di eseguire una sequenza di istruzioni che manipolano dei simboli su un nastro. Una MdT può essere vista come una macchina astratta che utilizza un nastro infinito e un insieme finito di simboli per eseguire un programma che definisce una determinata funzione. In modo simile, una funzione parziale ricorsiva può essere vista come una sequenza di istruzioni che definiscono come calcolare una determinata funzione a partire da alcune funzioni di base.

La corrispondenza tra le MdT e le FPR è stata dimostrata attraverso la costruzione di una MdT universale, ovvero una MdT in grado di simulare il comportamento di qualsiasi altra MdT. Questa MdT universale può essere utilizzata per definire una funzione parziale ricorsiva che rappresenta il comportamento di qualsiasi MdT.

[_Torna all'indice_](#Funzioni%20ricorsive)

---

### Forma normale di Kleene 
Per ogni funzione $φ ∈ \mathcal{PR}$ (o equivalentemente Turing calcolabile) esistono $f, g ∈ \mathcal{P}$ tali che
$$
φ = λx\; . \; f((μt \;. \; g(t,x) = 0), x).
$$

[_Torna all'indice_](#Funzioni%20ricorsive)

