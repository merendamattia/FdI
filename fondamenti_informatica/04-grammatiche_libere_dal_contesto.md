# Grammatiche libere dal contesto
```toc
```
---

#todo 
- [ ] da sistemare le diciture in latex

## Definizione formale
Una <mark style="background: #FFB86CA6;">grammatica</mark> è un insieme di regole che oermettono di generare un linguaggio. 
Le grammatiche sono composte da un insieme di simboli chiamati <mark style="background: #ABF7F7A6;">terminali</mark> (o parole del linguaggio, es. lettere alfabeto) e un insieme di simboli chiamati <mark style="background: #ABF7F7A6;">non terminali</mark> (o categorie sintattiche, es. nomi, verbi, aggettivi, ...) che rappresentano classi di parole o frasi.

<mark style="background: #BBFABBA6;">Le grammatiche libere dal contesto (CF)</mark>, o grammatiche *context-free* in inglese, sono un tipo di grammatica formale in cui ogni regola di produzione ha la forma $A → α$, dove $A$ è un simbolo non terminale e $α$ è una stringa di simboli terminali e/o non terminali. 
In altre parole, in una grammatica *context-free*, ogni non terminale può essere sostituito con qualsiasi stringa di simboli terminali e non terminali.

### A cosa servono e perchè sono importanti?
Le grammatiche *context-free* <mark style="background: #FFB8EBA6;">sono importanti perché</mark> sono utilizzate per descrivere la sintassi di molti linguaggi di programmazione, dove le regole grammaticali definiscono come costruire programmi corretti sintatticamente. Inoltre, le grammatiche *context-free* sono utilizzate in molte altre applicazioni, come il parsing di linguaggi naturali, l'analisi sintattica di frasi, la definizione di formati di file, e molto altro ancora.

Per quanto riguarda il loro utilizzo nel campo della programmazione, le grammatiche *context-free* sono spesso utilizzate per la generazione di compilatori e interpreti. In particolare, vengono utilizzate per definire la sintassi di un linguaggio di programmazione, cioè come vengono costruite le espressioni e le istruzioni in quel linguaggio. Questo è importante perché un compilatore o un interprete devono essere in grado di capire il codice scritto in un certo linguaggio di programmazione e tradurlo in un formato comprensibile per il computer.

Inoltre, le grammatiche *context-free* possono essere utilizzate anche per verificare la correttezza sintattica di un programma, ovvero per verificare che il codice scritto rispetti le regole grammaticali del linguaggio di programmazione. Questo è importante perché consente di identificare eventuali errori di sintassi nel codice prima della sua esecuzione, riducendo il rischio di errori e migliorando la sicurezza del programma.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

### Notazioni generali
![[grammatiche_notazioni_generali.png | 700]]

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

### Produzione
In una grammatica formale, una <mark style="background: #D2B3FFA6;">produzione</mark> (o regola di produzione) è una descrizione formale di come una stringa di simboli può essere trasformata in un'altra stringa di simboli. Le produzioni sono utilizzate per definire la struttura sintattica della lingua descritta dalla grammatica.

Una produzione è rappresentata da una regola della forma $A → B$, dove $A$ è un simbolo non terminale e $B$ è una stringa di simboli terminali e/o non terminali. La produzione indica che il simbolo $A$ può essere sostituito con la stringa $B$.

Ad esempio, consideriamo la seguente grammatica *context-free*:
$$S → aSb \;| \; ε$$
In questa grammatica, $S$ è un simbolo non terminale e $a$, $b$ sono simboli terminali. Questa grammatica descrive un linguaggio che contiene tutte le stringhe di $a$ e $b$ che sono bilanciate rispetto al numero di $a$ e $b$, ovvero tutte le stringhe in cui il numero di a è uguale al numero di $b$.

La prima produzione $S → aSb$ indica che il simbolo $S$ può essere sostituito con la stringa $aSb$, ovvero che possiamo aggiungere un $a$ all'inizio e un $b$ alla fine della stringa $S$. La seconda produzione $S → ε$ indica che il simbolo $S$ può essere sostituito con la stringa vuota, ovvero che la stringa può essere lasciata vuota.

Utilizzando queste produzioni, possiamo derivare tutte le stringhe del linguaggio, partendo dal simbolo iniziale $S$ e applicando le produzioni in modo ricorsivo. 
Ad esempio, partendo dal simbolo $S$, possiamo derivare la stringa $abb$ in questo modo:
$$S → aSb → aaSbb → aabbb$$
In questo modo, le produzioni sono fondamentali per la definizione della grammatica e per la generazione di tutte le stringhe che appartengono al linguaggio descritto dalla grammatica stessa.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

## Linguaggio generato
Il <mark style="background: #FFB86CA6;">linguaggio generato da una grammatica</mark> è l'insieme di tutte le stringhe che possono essere generate dalla grammatica stessa, seguendo le sue regole di produzione.

In altre parole, il linguaggio generato da una grammatica è l'insieme di tutte le stringhe che possono essere ottenute partendo dal simbolo iniziale della grammatica e applicando le produzioni della grammatica in modo ricorsivo.

Ad esempio, consideriamo la seguente grammatica *context-free*:
```css
S -> AB
A -> a
B -> b | ε
```
Questa grammatica genera un linguaggio che contiene tutte le stringhe che iniziano con la lettera "a" e terminano con la lettera "b" oppure sono composte solo dalla lettera "a".

Possiamo generare le stringhe del linguaggio partendo dal simbolo iniziale S e applicando le produzioni della grammatica. Ad esempio, possiamo derivare la stringa "ab" in questo modo:
$$S → AB → aB → ab$$
La <mark style="background: #BBFABBA6;">nozione di derivazione di un passo</mark> è il processo di applicazione di una sola produzione della grammatica per generare una nuova stringa a partire da una stringa esistente.

Ad esempio, consideriamo la seguente grammatica *context-free*:
$$S → AB A → a B → b \;|  \; ε$$
Se abbiamo la stringa "a" e vogliamo derivare la stringa "ab", possiamo applicare una sola produzione $B → b$ per generare la nuova stringa "ab". Questo è un esempio di derivazione di un passo.

La derivazione di un passo è utile perché ci consente di generare nuove stringhe del linguaggio passo dopo passo, a partire dal simbolo iniziale o da altre stringhe già generate. In questo modo, possiamo generare tutte le stringhe del linguaggio generato dalla grammatica.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

### Equivalenza tra due grammatiche
<mark style="background: #ABF7F7A6;">Due grammatiche sono equivalenti se descrivono lo stesso linguaggio</mark>, ovvero se generano lo stesso insieme di stringhe. Ciò significa che se due grammatiche sono equivalenti, allora entrambe descrivono lo stesso insieme di stringhe, e ogni stringa generata da una delle due grammatiche può essere generata anche dall'altra grammatica.

Per verificare se due grammatiche sono equivalenti, ci sono diversi approcci. Uno di questi è quello di controllare se entrambe le grammatiche generano le stesse stringhe. Questo può essere fatto generando tutte le stringhe che possono essere generate dalle due grammatiche e confrontandole tra loro.

Un altro modo per verificare l'equivalenza tra due grammatiche è quello di convertirle entrambe in forme normali normali, ad esempio la [forma normale di Chomsky](https://it.wikipedia.org/wiki/Forma_normale_di_Chomsky) o la [forma normale di Greibach](https://it.wikipedia.org/wiki/Forma_normale_di_Greibach), e quindi confrontare le due forme normali. Le due grammatiche sono equivalenti se e solo se le loro forme normali sono equivalenti.

L'equivalenza tra due grammatiche è importante perché garantisce che descrivono lo stesso linguaggio e che quindi generano le stesse stringhe. Questo è essenziale per garantire la correttezza e la precisione nella descrizione del linguaggio. 

> Inoltre, l'equivalenza tra due grammatiche è importante per la progettazione di algoritmi di parsing e di altre tecniche di analisi del linguaggio, poiché queste tecniche devono funzionare in modo corretto per qualsiasi grammatica equivalente.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

## Alberi di derivazione
Un <mark style="background: #FFB86CA6;">albero di derivazione</mark> è una rappresentazione grafica di una derivazione di una stringa da parte di una grammatica. In altre parole, un albero di derivazione mostra come una data stringa può essere generata a partire dal simbolo iniziale della grammatica, seguendo le regole di produzione della grammatica stessa.

L'albero di derivazione è costituito da un insieme di nodi e archi, dove i nodi rappresentano i simboli della stringa generata e le produzioni della grammatica che vengono applicate, mentre gli archi rappresentano la relazione tra i simboli generati e i simboli della stringa.

In un albero di derivazione, il nodo radice rappresenta il simbolo iniziale della grammatica, mentre le foglie rappresentano i simboli terminali della stringa generata. Ogni nodo interno rappresenta invece l'applicazione di una produzione della grammatica.

In un albero di derivazione, ogni vertice, o nodo, ha un'<mark style="background: #BBFABBA6;">etichetta</mark> che indica il simbolo o la produzione della grammatica che il nodo rappresenta. L'etichetta è necessaria per capire il ruolo del nodo all'interno dell'albero e per ricostruire la derivazione della stringa.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

### Utilità e importanza
<mark style="background: #FFB8EBA6;">L'importanza</mark> degli alberi di derivazione è legata al fatto che ci consentono di comprendere meglio come una stringa può essere generata a partire da una grammatica. Inoltre, gli alberi di derivazione sono spesso utilizzati come strumento di analisi del linguaggio, ad esempio per verificare se una data stringa appartiene o meno al linguaggio generato dalla grammatica.

Un <mark style="background: #ABF7F7A6;">albero di derivazione con radici etichettate</mark> è un tipo particolare di albero di derivazione in cui ogni nodo è etichettato con la produzione della grammatica che viene applicata. Questo tipo di albero è utile perché consente di visualizzare in modo più chiaro le produzioni che vengono applicate durante la derivazione.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

### Esempio - Alberi di derivazione
Consideriamo la seguente grammatica context-free:
$$S → aSb \;| \;ε$$
Per generare la stringa "aabbb", possiamo costruire il seguente albero di derivazione:

![[alberi_derivazione_esempio.png | 400]]

In questo albero, il nodo radice rappresenta il simbolo iniziale S, mentre i nodi figli rappresentano le produzioni che sono state applicate. In questo caso, abbiamo applicato la produzione 
$S → aSb$, quindi abbiamo aggiunto un nodo "a" come figlio del nodo radice e un altro nodo S come secondo figlio del nodo radice. In seguito, abbiamo applicato la produzione $S → ε$ al secondo figlio del nodo radice, che ha quindi generato un nodo vuoto. Infine, abbiamo applicato la produzione $S → b$ al secondo figlio del nodo radice, che ha generato il nodo "b". Alla fine, abbiamo ottenuto la stringa "aabbb" concatenando i nodi terminali dell'albero.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

## Ambiguità delle derivazioni
Una derivazione di una stringa è detta <mark style="background: #FFB86CA6;">ambigua</mark> se esistono più alberi di derivazione per la stessa stringa generati dalla stessa grammatica. Questo accade quando una stringa può essere generata da una grammatica in modi diversi, ovvero attraverso differenti sequenze di produzioni.

Per esempio, consideriamo la grammatica context-free $$S → S + S \; |\; S * S \;|\; a$$che genera espressioni aritmetiche con addizione e moltiplicazione. Se consideriamo l'espressione "a + a * a", ci sono due possibili alberi di derivazione:

![[ambiguita_alberi_derivazioni.png | 600]]

<mark style="background: #ABF7F7A6;">In questo caso, la presenza di più alberi di derivazione per la stessa espressione genera ambiguità nella grammatica.</mark> Inoltre, è importante notare che l'albero di derivazione sinistro e quello destro generano espressioni aritmetiche diverse, poiché la prima espressione corrisponde a "(a+a)_a", mentre la seconda corrisponde a "a+(a*a)".

Una derivazione si dice sinistra <mark style="background: #FFB8EBA6;">(leftmost)</mark> se in ogni passo si sostituisce il simbolo non terminale più a sinistra nella derivazione, altrimenti è detta derivazione destra <mark style="background: #FFB8EBA6;">(rightmost)</mark>. Nel caso della grammatica precedente, l'albero di derivazione sinistro corrisponde ad una derivazione sinistra, mentre l'albero di derivazione destro corrisponde ad una derivazione destra.

Una <mark style="background: #BBFABBA6;">grammatica context-free è ambigua</mark> se esiste almeno una stringa che può essere generata in modo ambiguo. In questo caso, la grammatica può generare più di un albero di derivazione per almeno una stringa. Al contrario, se una grammatica può generare al massimo un albero di derivazione per ogni stringa, allora è detta univoca.

Un <mark style="background: #D2B3FFA6;">linguaggio context-free è detto inerentemente ambiguo</mark> se non esiste nessuna grammatica univoca che lo genera. In altre parole, tutti i possibili grammatiche per il linguaggio sono ambigue. Ad esempio, il linguaggio delle parole palindromiche su un alfabeto di due lettere è inerentemente ambiguo.

Un altro esempio:
![[linguaggio_ambiguo_esempio.png | 500]]

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

## Semplificazioni
Per restringere la forma delle produzioni permesse alle grammatiche *context-free* senza alterare la classe dei linguaggi riconosciuti, si possono applicare alcune trasformazioni standard:

1. [Forma normale di Chomsky:](#Forma%20normale%20di%20Chomsky) questa trasformazione permette di scrivere ogni produzione in una delle due forme seguenti: $A → BC$ o $A → a$, dove $A$, $B$ e $C$ sono simboli non terminali, e $a$ è un simbolo terminale. In questa forma normale, tutte le produzioni hanno due simboli non terminali o un simbolo terminale a destra, semplificando le operazioni di parsing.

2. [Eliminazione di simboli inutili:](#Eliminazione%20di%20simboli%20inutili) questa trasformazione consiste nell'eliminare tutti i simboli non terminali e terminali che non sono raggiungibili dalla produzione iniziale S. In questo modo, si eliminano simboli che non contribuiscono alla generazione di nessuna stringa del linguaggio.

3. [Eliminazione di ε-produzioni:](#Eliminazione%20di%20ε-produzioni) questa trasformazione consiste nell'eliminare tutte le produzioni della forma $A → ε$, dove $A$ è un simbolo non terminale. Questo può comportare la creazione di nuove produzioni per rappresentare le possibilità di avere o meno simboli non terminali.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

### Eliminazione di simboli inutili
Per eliminare i simboli inutili, si può utilizzare l'algoritmo seguente:
1. Trovare tutti i simboli non terminali che possono essere raggiunti dalla produzione iniziale S.
2. Trovare tutti i simboli non terminali e terminali che sono usati nelle produzioni trovate al primo passo.
3. Ripetere i passi 1 e 2 finché non ci sono più simboli non terminali o terminali da aggiungere alla lista trovata al passo 2.
4. Costruire una nuova grammatica utilizzando solo i simboli non terminali e terminali trovati al passo 2. Tutte le produzioni che utilizzano simboli non terminali o terminali che non sono in questa lista possono essere eliminate.

#### Esempio - Eliminazione simboli inutili
#todo 
- [ ] Da verifica la correttezza

Supponiamo di avere la seguente grammatica context-free:
```css
S → A | B
A → a
B → b | C
C → c | D
E → f
```
In questa grammatica, il simbolo iniziale è S. Tuttavia, il simbolo E non è mai utilizzato in nessuna produzione, quindi possiamo eliminarlo dalla grammatica. Inoltre, il simbolo D non è mai raggiunto da nessun simbolo non terminale, quindi anche questo simbolo è inutile e può essere eliminato.

Si può procedere nel seguente modo:
1. Trovare i simboli raggiungibili dalla S:
	- S è direttamente raggiungibile dalla S.
	- A e B sono direttamente raggiungibili dalla S.
	- C e E non sono raggiungibili dalla S.
2. Trovare i simboli generabili:
	- S, A, B, C e D sono generabili.
	- E non è generabile.
3. Trovare i simboli utilizzati:
	- S, A, B, C e D sono utilizzati.
	- E non è utilizzato.
4. Costruire la nuova grammatica senza i simboli inutili:
	- S → A | B
	- A → a
	- B → b | C
	- C → c
	- D non compare in nessuna produzione, quindi può essere eliminato.

La nuova grammatica risultante è equivalente a quella originale ma con i simboli inutili eliminati.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

### Eliminazione di ε-produzioni
Per eliminare le ε-produzioni, si può utilizzare l'algoritmo seguente:
1. Trovare tutti i simboli non terminali che possono generare ε, ovvero quelli che hanno una produzione della forma $A → ε$.
2. Per ogni simbolo non terminale A trovato, sostituire tutte le occorrenze di A in tutte le produzioni della grammatica con tutte le possibili combinazioni di simboli non terminali che generano ε, tranne A stesso.
3. Ripetere il passo 2 finché non ci sono più produzioni della forma $A → ε$ nella grammatica.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

#### Esempio - Eliminazione ε-produzioni
#todo 
- [ ] Da verifica la correttezza

Supponiamo di avere la seguente grammatica context-free con ε-produzioni:
```css
S → AB | ε
A → a | ε
B → b | ε
C → c
```
L'obiettivo è eliminare tutte le epsilon-produzioni senza alterare il linguaggio generato dalla grammatica.

Si può procedere nel seguente modo:
1.  Trovare tutti i simboli che generano ε:
	-  A e B generano ε.
2.  Calcolare tutti i possibili insiemi di simboli che generano ε:
	- Nessun simbolo oltre ad A e B genera ε.
3.  Costruire tutte le possibili combinazioni di simboli che generano ε:
	- A e B generano ε, quindi AB genera ε.
4.  Aggiungere le nuove produzioni:
	- $S → AB \;|\; A \;|\; B \;|\; ε$ (aggiungiamo $S → A$ e $S → B$ per includere le produzioni senza $A$ e senza $B$)
	- $A → a$
	- $B → b$
	- $C → c$

La nuova grammatica risultante è equivalente a quella originale ma senza ε-produzioni. Nota che la produzione $S → ε$ viene sostituita con $S → A \;|\; B \;|\; ε$, poiché entrambe generano la stringa vuota.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

## Forma normale di Chomsky
La <mark style="background: #FFB86CA6;">Forma Normale di Chomsky (CNF)</mark> è una forma particolare in cui si possono esprimere le grammatiche libere dal contesto (Context-Free Grammar o CFG). 
Una grammatica si dice essere in CNF se ogni sua produzione ha una delle seguenti due forme:
- $A → BC$ (dove $A$, $B$ e $C$ sono simboli non terminali)
- $A → a$ (dove $a$ è un simbolo terminale)

> In altre parole, ogni produzione deve avere un simbolo non terminale come testa e la sua coda deve essere composta da due simboli non terminali o da un singolo simbolo terminale.

<mark style="background: #BBFABBA6;">Il Teorema di Chomsky stabilisce che ogni linguaggio CF può essere generato da una grammatica in CNF.</mark> La dimostrazione di questo teorema utilizza la forma normale di Greibach, che è una forma particolare delle grammatiche CF, e dimostra che ogni grammatica in forma normale di Greibach può essere convertita in CNF.

<mark style="background: #ABF7F7A6;">L'algoritmo per trasformare una grammatica in CNF è il seguente:</mark>
1. Eliminare le produzioni che generano simboli terminali.
2. Eliminare le produzioni che generano epsilon-produzioni.
3. Eliminare le produzioni che generano simboli non raggiungibili.
4. Sostituire tutte le produzioni di lunghezza maggiore di 2 con produzioni binarie.
5. Sostituire ogni simbolo terminale con una produzione unaria.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

### Esempio - Forma normale di Chomsky
#todo 
- [ ] Da verifica la correttezza

Sia data la seguente grammatica:
```
S -> aA | B
A -> ε | aB
B -> cC | Bd
C -> d | BCc
```

In questa grammatica, il simbolo $a$ è un simbolo terminale, mentre $S$, $A$, $B$, e $C$ sono simboli non terminali. Inoltre, ci sono due epsilon-produzioni: $A → ε$ e $C → d$. Infine, il simbolo $d$ è un simbolo terminale, ma non è raggiungibile partendo dal simbolo iniziale $S$.

Per eliminare i simboli inutili, iniziamo eliminando i simboli non raggiungibili. Possiamo fare ciò in tre passaggi:
1.  Trovare i simboli raggiungibili dal simbolo iniziale $S$: poiché $S$ è direttamente raggiungibile, i simboli raggiungibili sono $S$, $a$, $B$, e $C$.
2.  Trovare i simboli raggiungibili da ogni simbolo non terminale trovato al passaggio precedente: partendo da $S$, i simboli raggiungibili sono $S$, $a$, $B$, $C$, $ε$, $d$, $Bd$, e $Cc$.
3.  Costruire una nuova grammatica che contiene solo i simboli raggiungibili dal simbolo iniziale: la nuova grammatica sarà la seguente:
```
S -> aA | B
A -> aB
B -> Bd
C -> BCc
```

A questo punto, possiamo eliminare le epsilon-produzioni. Iniziamo aggiungendo una nuova produzione per ogni epsilon-produzione trovata:
```
S -> aA | B
A -> aB | ε
B -> Bd
C -> d | BCc
```

A questo punto, possiamo eliminare i simboli non generativi. Iniziamo eliminando $A -> ε$, che genera la stringa vuota ma non è raggiungibile dal simbolo iniziale:
```
S -> aA | B
A -> aB
B -> Bd
C -> d | BCc
```

Infine, possiamo riscrivere le produzioni in forma normale di Chomsky. Per farlo, dobbiamo creare nuovi simboli non terminali per ogni simbolo terminale nella grammatica:
```
S -> X1A | B
A -> X2B | a
B -> Bd
C -> d | X3Cc
X1 -> a
X2 -> ε
X3 -> ε
```

In questa forma normale di Chomsky, ogni produzione ha la forma $X -> YZ$, dove $X$, $Y$, e $Z$ sono simboli non terminali.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

### Esempio del libro
![[forma_normale_chomsky.png]]

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

## Forma normale di Greibach
La <mark style="background: #FFB86CA6;">Forma Normale di Greibach (GNF)</mark> è una forma normale per le grammatiche formali, simile alla forma normale di Chomsky (CNF). Una grammatica si trova in GNF se tutte le produzioni sono nella forma $A → aB_1B_2 \cdot \cdot \cdot B_n$, dove $A$ è un simbolo non terminale, $a$ è un simbolo terminale e $B_1B_2 \cdot \cdot \cdot B_n$ sono simboli non terminali.

L'idea principale dell'algoritmo per la trasformazione di una grammatica in GNF è quella di utilizzare l'<mark style="background: #BBFABBA6;">unfolding</mark>, ovvero la sostituzione di un simbolo non terminale con la sua definizione nella grammatica. In particolare, l'unfolding viene applicato in modo iterativo fino a quando la grammatica non si trova nella forma desiderata.

<mark style="background: #BBFABBA6;">L'eliminazione della ricorsione sinistra</mark> è un'altra operazione fondamentale per la trasformazione di una grammatica in GNF. Una produzione $A → Aα$ viene considerata ricorsiva sinistra se $A$ compare come primo simbolo nella parte destra della produzione. 
Per eliminare la ricorsione sinistra, si utilizza una tecnica chiamata fattorizzazione sinistra.

La <mark style="background: #D2B3FFA6;">fattorizzazione sinistra</mark> consiste nell'identificare una produzione non terminale che ha due o più simboli non terminali nella parte destra e quindi riscriverla in modo da suddividerla in due o più produzioni più corte, dove solo il primo simbolo non terminale della produzione originale è presente nella parte destra della produzione.

Ad esempio, consideriamo la seguente produzione:
```
A -> BCD
```
Possiamo applicare la fattorizzazione sinistra suddividendo la produzione in due produzioni più corte come segue:
```
A -> BE 
E -> CD
```
In questo modo, abbiamo ridotto la lunghezza della produzione originale da tre a due simboli non terminali.

> In pratica, l'eliminazione della ricorsione sinistra e l'unfolding vengono applicati in modo alternato fino a quando la grammatica raggiunge la forma normale di Greibach.

L'importanza della forma normale di Greibach sta nel fatto che essa semplifica notevolmente l'analisi e la comprensione della grammatica. In particolare, permette di effettuare l'analisi sintattica in modo più efficiente e preciso.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

### Grammatiche lineari destre
Le <mark style="background: #FFB86CA6;">grammatiche lineari destre</mark>, anche chiamate grammatiche a produzioni lineari destre o grammatiche regolari destre, sono una classe di grammatiche formali. Queste grammatiche hanno la particolarità di avere ogni produzione nella forma:
$$A → aB \;\;\text{o}\;\; A → a$$
dove $A$ e $B$ sono simboli non terminali, a è un simbolo terminale e la parte destra della produzione è composta al massimo da un simbolo non terminale seguito da zero o più simboli terminali.

In altre parole, ogni produzione delle grammatiche lineari destre ha un unico simbolo non terminale alla fine della parte destra. Questo significa che ogni derivazione di una stringa a partire da una grammatica lineare destra procede da sinistra verso destra.

Le grammatiche lineari destre sono una sottoclasse delle grammatiche context-free (CF) e, come tali, possono essere utilizzate per descrivere linguaggi formali. In particolare, <mark style="background: #BBFABBA6;">ogni linguaggio regolare</mark> (cioè un linguaggio riconosciuto da un automa finito deterministico) <mark style="background: #BBFABBA6;">può essere generato da una grammatica lineare destra.</mark>

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)

---

### Esempio - Forma normale di Greibach
#todo 
- [ ] Da verifica la correttezza

Un esempio di applicazione dell'algoritmo per la trasformazione di una grammatica in GNF:
```
S → aA | bB 
A → aS | bAA 
B → bS | aBB
```

1. Eliminazione della ricorsione sinistra in $A$: 
```
A → aS | bAA 
A → baSA' | ε 
A' → aSA' | bAA'
```

2.  Unfolding della produzione $S → aA$: 
```
S → aA | bB 
S → a(baSA' | ε) | bB 
S → abaSA' | bB
```

3.  Unfolding della produzione $B → aBB$: 
```
S → abaSA' | b(aBB | bS) 
S → abaSA' | baBB | bbS
```

4.  Trasformazione delle produzioni in GNF: 
```
S → aA1 | bB1 
A → aS1 | bA2 
A1 → bA' | ε 
A' → aS1A' | bA2A' 
B → bS2 | aB3 
S1 → bS1A' | ε 
S2 → aB3 | bS2S2 
B3 → bS2B3 | ε
```    

La grammatica risultante è ora in GNF.

[_Torna all'indice_](#grammatiche%20libere%20dal%20contesto)