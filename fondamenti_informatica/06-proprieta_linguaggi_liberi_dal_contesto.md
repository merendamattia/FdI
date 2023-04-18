# Proprietà dei linguaggi liberi dal contesto
```toc
```
---

Per i linguaggi CF valgono delle proprietà simili a quelle viste per i [linguaggi regolari](obsidian://open?vault=Uni&file=FdI%2Ffondamenti_informatica%2F03-proprieta_linguaggi_regolari).

## Pumping lemma per i linguaggi CF
Il pumping lemma per i linguaggi CF afferma che per ogni linguaggio CF $L$ esiste un numero naturale $n$ tale che, se una stringa $z$ di $L$ ha una lunghezza maggiore o uguale a $n$, allora $z$ può essere suddivisa in cinque parti, `z = uvwxy`, soddisfacendo le seguenti condizioni:
1.  $|vx| ≥ 1$
2.  $|vwx| ≤ n$
3.  per ogni $i ≥ 0$, la stringa $uv^iwx^iy$ appartiene a $L$.

In altre parole, se una stringa del linguaggio CF ha una lunghezza sufficientemente grande, allora è possibile trovare una sottostringa "pompabile" all'interno di essa che, ripetuta qualsiasi numero di volte, porta ad una nuova stringa che non appartiene più al linguaggio.

Se una stringa $z$ non rispetta queste condizioni, allora non può essere generata dal linguaggio CF $L$. In questo modo, il pumping lemma può essere utilizzato per dimostrare che un certo linguaggio non è CF, poiché se esiste una stringa $z$ che non può essere pompata, allora il linguaggio $L$ non può essere generato da una grammatica CF.

### Dimostrazione
![[dimostrazione_pumping_lemma.jpeg]]![[dimostrazione_pumping_lemma_2.jpeg]]

[_Torna all'indice_](#Proprietà%20dei%20linguaggi%20liberi%20dal%20contesto)

### Esempio
![[FdI/fondamenti_informatica/data/images/proprieta_linguaggi_CF/esempio1.png]]![[FdI/fondamenti_informatica/data/images/proprieta_linguaggi_CF/esempio2.png]]

[_Torna all'indice_](#Proprietà%20dei%20linguaggi%20liberi%20dal%20contesto)

---

## Proprietà di chiusura
<mark style="background: #FFB86CA6;">I linguaggi CF sono chiusi rispetto all’unione, alla concatenazione, ed alla chiusura di Kleene.</mark>
La proprietà di chiusura rispetto all'unione, alla concatenazione e alla chiusura di Kleene è una proprietà importante dei linguaggi formali e implica che, se due linguaggi sono CF, allora la loro unione, la loro concatenazione e la loro chiusura di Kleene sono anche CF.

In altre parole, se abbiamo due linguaggi CF $L_1$ e $L_2$, allora:
-   $L_1 ∪ L_2$ è CF (CF è chiuso rispetto all'unione).
-   $L_1 \cdot L_2$ è CF (CF è chiuso rispetto alla concatenazione).
-   $L_1^*$ è CF (CF è chiuso rispetto alla chiusura di Kleene).

![[dimostrazione_chiusura.png]]

<mark style="background: #ABF7F7A6;">I linguaggi CF non sono chiusi rispetto all’intersezione.</mark>
Ciò significa che, dato un qualsiasi paio di linguaggi CF, la loro intersezione potrebbe non essere un linguaggio CF. In altre parole, la classe dei linguaggi CF non è chiusa rispetto all'operazione di intersezione. 
Questo può essere dimostrato tramite un controesempio: si considerino ad esempio i due linguaggi CF 
$$
L_1 = \{ \; a^n b^n c^n \;|\; n ≥ 1 \;\}, \;\;L_2 = \{ \; a^n b^n \; | \; n ≥ 1 \; \}
$$
Entrambi sono noti per essere CF, ma la loro intersezione  $L_1 ∩ L_2 = \{ \; a^n b^n c^n \;|\; n ≥ 1 \;\}$ non è CF. Questo dimostra che la classe dei linguaggi CF non è chiusa rispetto all'intersezione.

<mark style="background: #BBFABBA6;">I linguaggi CF non sono chiusi rispetto alla complementazione.</mark>
Significa che se $L$ è un linguaggio CF, il suo complemento $L'$ (cioè l'insieme di tutte le stringhe che non appartengono a $L$) potrebbe non essere un linguaggio CF. In altre parole, non è sempre possibile costruire una grammatica CF che generi esattamente tutte le stringhe che non appartengono a $L$.

[_Torna all'indice_](#Proprietà%20dei%20linguaggi%20liberi%20dal%20contesto)

---

## Algoritmi di decisione

### Teorema 8.7 (Vuoto, Finito, Infinito) 
Data una grammatica CF $G = ⟨V, T, P, S⟩$, i problemi: 
1. $L(G) = \varnothing$, 
2. $L(G)$ è finito, 
3. $L(G)$ è infinito, 

sono decidibili.

> In altre parole, per ogni grammatica CF, è possibile stabilire in modo algoritmico se il linguaggio generato da essa è vuoto, finito o infinito. Ciò significa che esiste un algoritmo deterministico che prende in input una grammatica CF e risolve uno dei tre problemi di cui sopra in un tempo finito.

#### Dimostrazione
(1) Per decidere se $L(G) = \varnothing$, possiamo costruire un algoritmo che genera tutte le stringhe che possono essere derivate dalla grammatica $G$, e controllare se ce n'è almeno una che appartiene all'alfabeto terminale $T$. Se non c'è alcuna stringa terminale, allora $L(G) = \varnothing$. In caso contrario, $L(G)$ non è vuoto.

(2) e (3) Per decidere se $L(G)$ è finito, possiamo utilizzare l'algoritmo di pumping lemma per i linguaggi CF. In particolare, supponiamo di avere una stringa $w ∈ L(G)$ tale che $|w| > n$, dove $n$ è il numero di variabili non terminali nella grammatica. Possiamo quindi scomporre la stringa $w$ come $w = uvxyz$, dove $|vy| > 0$ e $|vxy| ≤ n$. Se esiste almeno una tale scomposizione tale che anche le stringhe $uv^ixy^iz$ sono in $L(G)$ per ogni $i ≥ 0$, allora $L(G)$ è infinito. In caso contrario, $L(G)$ è finito.

[_Torna all'indice_](#Proprietà%20dei%20linguaggi%20liberi%20dal%20contesto)

---

### Teorema 8.8 (Appartenenza)
Data una grammatica CF $G = ⟨V,T,P,S⟩$, e una stringa $z$, il problema $z ∈ L(G)$ è decidibile.

Questo teorema afferma che, data una grammatica context-free $G$ e una stringa $z$, è possibile decidere se $z$ appartiene al linguaggio generato dalla grammatica $L(G)$. In altre parole, si può determinare se la stringa $z$ può essere generata a partire dal simbolo iniziale $S$ della grammatica $G$ applicando le produzioni di $G$.

La dimostrazione del Teorema 8.8 si basa sull'uso dell'*Algoritmo CYK* (Cocke-Younger-Kasami), che consente di decidere se una stringa appartiene al linguaggio generato da una grammatica CF in tempo polinomiale. L'Algoritmo CYK si basa sull'utilizzo di una tabella di parsing, dove le celle indicano le sottostringhe della stringa di input e gli stati della grammatica che possono generare tali sottostringhe. Attraverso l'uso di una procedura ricorsiva, l'algoritmo riempie la tabella di parsing e determina se la stringa di input può essere generata dalla grammatica.

[_Torna all'indice_](#Proprietà%20dei%20linguaggi%20liberi%20dal%20contesto)

---

### Algoritmo CYK (Cocke-Younger-Kasami)
L'algoritmo per determinare se una stringa $z$ appartiene al linguaggio generato da una grammatica CF $G = ⟨V, T, P, S⟩$ è basato sull'idea di utilizzare l'analisi *LL* (Left-to-Right, Leftmost derivation) della stringa $z$.

L'algoritmo procede nel seguente modo:
1. Costruire la tabella di parsing LL della grammatica $G$, la quale consente di effettuare l'analisi sintattica della stringa $z$.
2. Inizializzare lo stack di parsing con il simbolo iniziale $S$.
3. Leggere il primo simbolo di $z$.
4. Finché lo stack non è vuoto e la lettura di $z$ non è terminata, ripetere i seguenti passi: 
	1. Se il simbolo in cima allo stack è un simbolo terminale e corrisponde al simbolo letto da $z$, allora rimuoverlo dallo stack e leggere il prossimo simbolo di $z$.
	2. Se il simbolo in cima allo stack è un simbolo non terminale, allora cercare nella tabella di parsing LL la produzione appropriata per quel simbolo non terminale e il simbolo letto da z. Se esiste una produzione, allora sostituire il simbolo non terminale con i simboli della produzione (in ordine inverso) nello stack di parsing. Altrimenti, la stringa $z$ non appartiene al linguaggio generato da $G$.
5. Se alla fine dello stack rimane solo il simbolo iniziale S e la lettura di z è terminata, allora la stringa z appartiene al linguaggio generato da G. Altrimenti, la stringa z non appartiene al linguaggio generato da $G$.

L'algoritmo sfrutta il fatto che, se una grammatica è CF, allora la sua analisi LL riesce sempre a produrre una derivazione sinistra per ogni stringa del linguaggio generato. Questo fatto consente di determinare se una stringa appartiene al linguaggio generato dalla grammatica in modo efficiente.

> Questo algoritmo ha complessità esponenziale.

[_Torna all'indice_](#Proprietà%20dei%20linguaggi%20liberi%20dal%20contesto)