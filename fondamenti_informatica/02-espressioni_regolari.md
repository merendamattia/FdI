# Espressioni regolari
```toc
```
---
<mark style="background: #FFF3A3A6;">TODO: da sistemare le espressioni in latex</mark>

## Sintassi e semantica
La sintassi e la semantica sono concetti fondamentali dell'informatica teorica e sono strettamente correlati.

La <mark style="background: #FFB86CA6;">sintassi</mark> si riferisce alla struttura formale di un linguaggio, ovvero alle regole che definiscono la grammatica del linguaggio. Ad esempio, nella teoria delle espressioni regolari, la sintassi definisce le regole per la costruzione di espressioni regolari, come l'uso di parentesi, caratteri speciali come l'asterisco `*` e il punto `.` e gli operatori di unione `+` e concatenazione '$\cdot$' .

La <mark style="background: #FFB86CA6;">semantica</mark>, d'altra parte, si riferisce al significato del linguaggio, ovvero a ciò che il linguaggio esprime e come viene interpretato. Nella teoria delle espressioni regolari, la semantica definisce il significato delle espressioni regolari, ovvero l'insieme di stringhe che soddisfano l'espressione regolare.

Ad esempio, consideriamo l'espressione regolare `(a+b)*abb`, dove '`+`' indica l'operatore di unione e '`*`' indica la ripetizione zero o più volte. La sintassi di questa espressione regolare definisce la struttura formale dell'espressione regolare, ovvero l'uso di parentesi e operatori. La semantica definisce il significato dell'espressione regolare, ovvero l'insieme di tutte le stringhe che iniziano con zero o più occorrenze di `"a"` o `"b"` e terminano con la sequenza `"abb".`

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
- Σ∗ è esso stesso un linguaggio, il linguaggio formato da tutte le stringhe su Σ;
- essendo ∅ sottoinsieme di qualsiasi altro insieme, ∅ ⊆ Σ∗ dunque ∅ è un linguaggio su qualsiasi alfabeto;
- essendo ε la stringa nulla su qualsiasi alfabeto Σ, { ε } ⊆ Σ∗ dunque { ε } è un linguaggio su qualsiasi alfabeto.

Siano Σ un alfabeto e $L_1$, $L_2$ ⊆ $Σ^*$ linguaggi, la <mark style="background: #FFB86CA6;">concatenazione</mark> di $L_1$ e $L_2$, denotata con L1 · L2, è l’insieme:
$$L_1 \cdot L_2 :={x \cdot y | x ∈ L_1, y∈L_2}.$$
<mark style="background: #FFF3A3A6;">TODO: da aggiungere definizione concatenazione iterata</mark>
> La *concatenazione* viene utilizzata per unire due o più pattern di caratteri in un'unica espressione regolare.

<mark style="background: #FFB86CA6;">La chiusura di Kleene</mark> di $L$, denotata come $L^*$ è l'insieme: <mark style="background: #FFF3A3A6;">TODO: da aggiungere formula in LaTeX</mark>
mentre la chiusura positiva di $L$, denotata come $L^+$ è l'insieme:  <mark style="background: #FFF3A3A6;">TODO: da aggiungere formula in LaTeX</mark>

> La *chiusura di Kleene* è un simbolo `*` che viene aggiunto alla fine di un elemento o di un gruppo di elementi nell'espressione regolare per indicare che l'elemento o il gruppo di elementi può essere ripetuto zero o più volte.

<mark style="background: #ABF7F7A6;">Proprietà della chiusura di Kleene:</mark>
1. Idempotenza: $(L^*)^* = L^*L^* = L^*.$
2. Monotonia: $L ⊆ M ⇒ L^∗ ⊆ M^∗$.
3. Estensività: $L ⊆ L^∗$.

Quindi la chiusura di Kleene è un *UCO*.

> *UCO* è l'acronimo di *"Unione, Chiusura di Kleene e Concatenazione"*, che sono le tre operazioni fondamentali nell'algebra delle espressioni regolari. Queste operazioni sono considerate UCO in quanto sono sufficienti per definire tutte le espressioni regolari possibili.

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