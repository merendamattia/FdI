# Espressioni regolari
```toc
```
---

## Sintassi e semantica
La sintassi e la semantica sono concetti fondamentali dell'informatica teorica e sono strettamente correlati.

La <mark style="background: #FFB86CA6;">sintassi</mark> si riferisce alla struttura formale di un linguaggio, ovvero alle regole che definiscono la grammatica del linguaggio. Ad esempio, nella teoria delle espressioni regolari, la sintassi definisce le regole per la costruzione di espressioni regolari, come l'uso di parentesi, caratteri speciali come l'asterisco `*` e il punto `.`, e gli operatori di unione `+` e concatenazione '$\cdot$' .

La <mark style="background: #FFB86CA6;">semantica</mark>, d'altra parte, si riferisce al significato del linguaggio, ovvero a ciò che il linguaggio esprime e come viene interpretato. Nella teoria delle espressioni regolari, la semantica definisce il significato delle espressioni regolari, ovvero l'insieme di stringhe che soddisfano l'espressione regolare.

Ad esempio, consideriamo l'espressione regolare $(a+b)^*abb$, dove '`+`' indica l'operatore di unione e '`*`' indica la ripetizione zero o più volte. La sintassi di questa espressione regolare definisce la struttura formale dell'espressione regolare, ovvero l'uso di parentesi e operatori. La semantica definisce il significato dell'espressione regolare, ovvero l'insieme di tutte le stringhe che iniziano con zero o più occorrenze di `"a"` o `"b"` e terminano con la sequenza `"abb".`

In <mark style="background: #FFF3A3A6;">sintesi</mark>, la sintassi si riferisce alla forma del linguaggio, mentre la semantica si riferisce al significato del linguaggio. La sintassi e la semantica sono entrambe importanti per comprendere il funzionamento dei linguaggi formali come le espressioni regolari.

[_Torna all'indice_](#espressioni%20regolari)

### Semantica composizionale
La semantica composizionale <mark style="background: #ABF7F7A6;">è un'approccio alla definizione del significato di un'espressione complessa come combinazione di significati di parti più semplici dell'espressione.</mark> In altre parole, il significato di un'espressione complessa è determinato dalla composizione dei significati delle sue parti costituenti.

Questo approccio si basa sulla nozione di <mark style="background: #BBFABBA6;">composizione</mark>, ovvero sulla capacità di combinare le parti per creare un tutto più grande. Ad esempio, nella matematica, il significato di un'espressione aritmetica complessa come `"3 + 4 * 5"` può essere determinato dalla composizione dei significati delle sue parti costituenti: il significato di `"4 * 5"` viene determinato dalla moltiplicazione di `4` e `5`, che dà `20`, mentre il significato dell'espressione complessiva viene determinato dalla somma di `3` e `20`, che dà `23`.

La semantica composizionale è molto importante nell'ambito dei linguaggi di programmazione, dove le espressioni sono spesso complesse e composte da molte parti. In questo caso, il significato di un programma può essere determinato dalla composizione dei significati delle sue parti costituenti, come le variabili, le istruzioni e le funzioni.

In generale, l'approccio alla semantica composizionale può semplificare la comprensione del significato di un'espressione complessa e fornire una base solida per la verifica formale e la validazione dei programmi.

[_Torna all'indice_](#espressioni%20regolari)

---

## Operazioni sui linguaggi
<mark style="background: #BBFABBA6;">L'algebra delle espressioni regolari</mark> è un insieme di regole che definiscono le operazioni aritmetiche e logiche applicabili alle espressioni regolari. Le operazioni principali dell'algebra delle espressioni regolari includono l'unione, la concatenazione e la ripetizione.

> In matematica, l'*algebra* è un ramo che studia le regole e le proprietà delle operazioni aritmetiche e algebriche applicate ai numeri e alle quantità in generale.

Sia Σ un alfabeto, un <mark style="background: #FFB86CA6;">linguaggio formale</mark> (in breve linguaggio, spesso indicato con L), è un insieme formato dalle stringhe su Σ, quindi vale che:
$$L ⊆ Σ^*.$$
> Un *linguaggio formale* è un insieme di stringhe di caratteri che rispettano determinate regole sintattiche.

Notare che:
- $Σ^*$ è esso stesso un linguaggio, il linguaggio formato da tutte le stringhe su Σ;
- essendo ∅ sottoinsieme di qualsiasi altro insieme, ∅ $⊆ Σ^*$ dunque ∅ è un linguaggio su qualsiasi alfabeto;
- essendo ε la stringa nulla su qualsiasi alfabeto Σ, $\{ ε \} ⊆ Σ^*$ dunque { ε } è un linguaggio su qualsiasi alfabeto.

Siano Σ un alfabeto e $L_1$, $L_2$ ⊆ $Σ^*$ linguaggi, la <mark style="background: #FFB86CA6;">concatenazione</mark> di $L_1$ e $L_2$, denotata con L1 · L2, è l’insieme:
$$L_1 \cdot L_2 :=\left\{ {x \cdot y \;|\; x ∈ L_1, y∈L_2} \right\}.$$

> La *concatenazione* viene utilizzata per unire due o più pattern di caratteri in un'unica espressione regolare.

Definiamo ora la <mark style="background: #BBFABBA6;">*Concatenazione iterata*</mark>:
$$
\begin{equation*}
	\left\{\begin{array}{ll}
		L^0 &= \{\varepsilon\} \\
		L^{i+1} &= LL^i
	\end{array}\right. \quad \forall i \in \mathbb{N}
\end{equation*}
$$
<mark style="background: #FFB86CA6;">La chiusura di Kleene</mark> di $L$, denotata come $L^*$ è l'insieme: 
$$
	L^* = \bigcup_{i \geq 0}{L^i}
$$
mentre la chiusura positiva di $L$, denotata come $L^+$ è l'insieme: 
$$
	L^+ = \bigcup_{i \geq 1}{L^i}
$$
> La *chiusura di Kleene* è un simbolo `*` che viene aggiunto alla fine di un elemento o di un gruppo di elementi nell'espressione regolare per indicare che l'elemento o il gruppo di elementi può essere ripetuto zero o più volte.

<mark style="background: #ABF7F7A6;">Proprietà della chiusura di Kleene:</mark>
1. Idempotenza: $(L^*)^* = L^*.$
2. Monotonia: $L ⊆ M ⇒ L^∗ ⊆ M^∗$.
3. Estensività: $L ⊆ L^∗$.

Quindi la chiusura di Kleene è un **UCO** (*Upper Closure Operator*) .

> *UCO* è l'acronimo di *"Operatore di chiusura superiore"*, e comprende le tre operazioni fondamentali nell'algebra delle espressioni regolari (idempotenza, monotonia ed estensività). 
> Queste operazioni sono considerate UCO in quanto sono sufficienti per definire tutte le espressioni regolari possibili.

[_Torna all'indice_](#espressioni%20regolari)

---

## Definizione formale
Sia Σ un alfabeto. Le <mark style="background: #FFB86CA6;">espressioni regolari</mark> su Σ e gli insiemi che esse denotano sono definiti ricorsivamente nel modo seguente:
1. ∅ è una espressione regolare che denota l’insieme vuoto.
2. ε è una espressione regolare che denota l’insieme {ε}.
3. Per ogni simbolo $a ∈ Σ$, $a$ è una espressione regolare che denota l’insieme `{a}`.
4. Se r e s sono espressioni regolari su Σ, r · s è una espressione regolare su Σ.
5.  Se r e s sono espressioni regolari su Σ, r + s è una espressione regolare su Σ.
6.  Se r è una espressione regolare su Σ, $r^∗$ è una espressione regolare su Σ.

> Un'*espressione regolare* è una notazione formale utilizzata per descrivere pattern di stringhe. In pratica, è un insieme di simboli che permette di definire in modo preciso quali stringhe appartengono a un determinato insieme.

### Sintassi e semantica
Ci sono altri modi di descrivere la <mark style="background: #FFB8EBA6;">sintassi</mark> di una espressione regolare; uno di questi utilizza la grammatica in forma <mark style="background: #BBFABBA6;">BNF</mark> (*[Backus-Naur form](https://it.wikipedia.org/wiki/Backus-Naur_Form)*).
Dato $\Sigma := \left\{a_1 \ldots a_n \right\}$ un alfabeto, un'espressione regolare su $\Sigma$ è una qualunque stringa generata dalla seguente grammatica
$$
	E := a_1 \;|\; \ldots \;|\; a_n \;|\; 
		\underline{\varepsilon} \;|\; \underline{\varnothing} \;|\;
		E_1 \underline{+} E_2 \;|\; E_1 \underline{\cdot} E_2 \;|\; E^*
$$

Per quanto riguarda la <mark style="background: #FFB8EBA6;">semantica</mark> di un'espressione regolare, usiamo la definizione di "*fa match*".
Dato $\Sigma := \left\{a_1 \ldots a_n \right\}$ un alfabeto e $r$ un'espressione regolare su $\Sigma$, si dice che una stringa $x \in \Sigma^*$ fa match con $r$, scritto $x \lessdot r$, se:
1. $a \lessdot a$, se $a \in \Sigma$ (un simbolo dell'alfabeto fa match con se stesso)
2. $\varepsilon \lessdot \underline{\varepsilon}$ (la stringa vuota fa match con il simbolo che la denota)
3. $x \, \mathrlap{\nless}\,\cdot \, \underline{\varnothing}$, per ogni $x \in \Sigma^*$
4. $x \lessdot r_1 \underline{+} r_2$, se $x \lessdot r_1$ o $x \lessdot r_2$
5. $x \lessdot r_1 \underline{\cdot} r_2$, se esistono $y,z \in \Sigma^*$ tali che $x=y \cdot z ,\; y \lessdot r_1,\, z \lessdot r_2$
6. $x \lessdot r^*$, se $x \lessdot \varepsilon$ oppure esistono $y,z \in \Sigma^*$ tali che $x=y \cdot z ,\; y \lessdot r,\, z \lessdot r^*$

Dato $\Sigma$ un alfabeto e $r$ una espressione regolare su di esso, definiamo il <mark style="background: #FFB86CA6;">linguaggio denotato da una espressione regolare</mark> $r$ come
$$
	L(r) = [\![ r ]\!] := \left\{ {x \in \Sigma^* \;|\; x \lessdot r} \right\}  
$$
quindi un <mark style="background: #ABF7F7A6;">linguaggio <i>L</i> è regolare</mark> se esiste almeno una espressione regolare $r$ che lo denota, ovvero $$L = L(r).$$
[_Torna all'indice_](#espressioni%20regolari)

---

## Equivalenza tra DFA e ER
Sia $r$ una espressione regolare. Allora esiste un $\epsilon \text{-NFA } M$ tale che $L(M) = L(r)$.   
[[dim_th_4-4.pdf|Dimostrazione teorema 4.4 (McNaughton & Yamada, 1960).]]

> Il teorema di McNaughton e Yamada stabilisce che ogni linguaggio regolare può essere rappresentato da un'espressione regolare e da un deterministico automa a stati finiti (DFA), e viceversa. In altre parole, ogni linguaggio regolare può essere descritto in modo equivalente da un'espressione regolare o da un DFA.

> La dimostrazione del teorema si basa sulla costruzione di un DFA per un'espressione regolare data e viceversa.
> L'idea di base dell'*algoritmo di eliminazione degli stati* è quella di eliminare uno stato alla volta dal DFA, sostituendolo con un'espressione regolare che descrive il comportamento del DFA senza lo stato eliminato. Questa espressione regolare può essere costruita combinando le transizioni in ingresso e in uscita dallo stato eliminato in un modo specifico, in modo da mantenere l'equivalenza con il DFA originale.

Sia $M$ un DFA. Allora esiste una espressione regolare $r$ tale che $L(M) = L(r)$. 

[[dim_th_4-6.pdf|Dimostrazione teorema 4.6]]

![[nfa-dfa-re.svg]]

[_Torna all'indice_](#espressioni%20regolari)