# Proprietà dei linguaggi regolari
```toc
```
---

Se un linguaggio è riconosciuto da un automa a stati finiti allora è un linguaggio regolare. Argomenti di questo capitolo saranno i principali risultati e metodi utili per stabilire se un dato linguaggio sia o meno regolare.

## Pumping Lemma
Sia $L$ un linguaggio regolare. Allora esiste una costante $n \in \mathbb{N}$ tale che per ogni $z \in L$ tale che $|z| \geq n$ esistono tre stringhe $u, v, w$ tali che:
1. $z = uvw$,
2. $|uv| \leq n$,
3. $|v| > 0$,
4. per ogni $i \geq 0$ vale che $uv^iw \in L$.

[[dim_lemma_5-1.pdf | Dimostrazione lemma 5.1 (Bar-Hillel, Perles, Shamir, 1961).]]

Corollario 5.2: $n$ del Lemma 5.1 può essere preso come numero di stati del più piccolo automa riconoscente $L$.
[[dim_coroll_5-2.pdf|Dimostrazione corollario 5.2.]]

> Il lemma afferma che se un linguaggio è regolare, allora esiste un intero positivo (chiamato "*pumping length*") tale che qualsiasi stringa del linguaggio che abbia una lunghezza maggiore di quella del *pumping length* può essere "*pompata*", ovvero può essere suddivisa in tre parti: una parte iniziale, una parte ripetuta un certo numero di volte e una parte finale, in modo che la parte ripetuta possa essere "gonfiata" o "scolpita" (pompata) in qualsiasi modo senza alterare il fatto che la stringa risultante sia ancora nel linguaggio.

> In altre parole, se un linguaggio è regolare, esiste una sorta di "motore interno" che fa sì che le parti ripetute possano essere "pompate" in modo che la stringa risultante sia ancora nel linguaggio. Se non esiste tale "motore interno", allora il linguaggio non può essere regolare.

Esempio:
![[linguaggio_non_regolare_esempio.png]]

Esempio:
![[linguaggio_non_regolare_esempio2.png]]

[_Torna all'indice_](#proprietà%20dei%20linguaggi%20regolari)

---

## Proprietà di chiusura
I linguaggi regolari sono chiusi rispetto alle operazioni di unione, concatenazione e chiusura di Kleene.

I linguaggi regolari sono chiusi rispetto alla operazione di complementazione. 
Ovvero, se $L ⊆ Σ^*$ è regolare, anche $\overline{\rm L} = Σ^* \ L$ è regolare.

I linguaggi regolari sono chiusi rispetto all’intersezione.

[[dim_th_5-6.pdf |Dimostrazione di questi tre teoremi (5.6, 5.7, 5.8).]]

> La proprietà di chiusura è un'altra importante proprietà dei linguaggi regolari. Essa stabilisce che se si prendono due linguaggi regolari, l'operazione di unione, concatenazione e chiusura di Kleene tra di essi produce un altro linguaggio regolare.

> In altre parole, se L1 e L2 sono due linguaggi regolari, allora anche L1 U L2 (unione), L1L2 (concatenazione) e L1* (chiusura di Kleene di L1) sono tutti linguaggi regolari.

> Ad esempio, se abbiamo due linguaggi regolari $L_1$ e $L_2$ che rappresentano rispettivamente le stringhe che iniziano con "a" e quelle che terminano con "b", possiamo utilizzare la proprietà di chiusura per ottenere un nuovo linguaggio regolare che rappresenta le stringhe che iniziano con "a" e terminano con "b", semplicemente concatenando $L_1$ e $L_2$.

Esempio:
![[chiusura_esempio.png]]

[_Torna all'indice_](#proprietà%20dei%20linguaggi%20regolari)

---

## Risultati di decidibilità
Un primo risultato scontato in questa classe di linguaggi è la decidibilità del <mark style="background: #FFB86CA6;">problema dell’appartenenza</mark>, ovvero: data una descrizione del linguaggio $L$ (mediante e.r. o automa) e una stringa $x$, decidere se $x ∈ L$ o meno. 
Se è data l'espressione regolare, possiamo prima calcolare l’automa.

Teorema (Vuoto-infinito). L’insieme delle stringhe accettate da un DFA $M$ con $n$ stati è:
1. non vuoto se e solo se accetta una stringa di lunghezza inferiore a $n$;
2. infinito se e solo se l’automa accetta una stringa di lunghezza $l$, $n ≤ l < 2n$.

[[dim_th_5-12.pdf|Dimostrazione teorema 5.12.]]

Sia $M$ DFA. Allora i problemi $L(M) = \varnothing$ e $L(M) \text{ è infinito}$ sono entrambi decidibili.
Teorema (Equivalenza). Dati due DFA $M_1$ e $M_2$, il problema di stabilire se $L(M_1) = L(M_2)$ è decidibile.
[[dim_th_5-14.pdf|Dimostrazione teorema 5.14.]]

> Dire che un *linguaggio regolare è decidibile* significa che esiste un algoritmo che, a partire da una qualsiasi stringa di input, determina in tempo finito se quella stringa appartiene o meno al linguaggio regolare.

> Ad esempio, il linguaggio regolare delle stringhe che contengono un numero pari di "0" è decidibile, perché possiamo scrivere un algoritmo che conta il numero di "0" nella stringa e determina se questo numero è pari o dispari. Al contrario, il linguaggio delle stringhe che contengono un numero primo di "0" non è decidibile.

[_Torna all'indice_](#proprietà%20dei%20linguaggi%20regolari)

--- 

## Teorema di Myhill-Nerode
Dato un insieme S, una relazione di equivalenza R $\subseteq$ S x S induce una partizione di S = S1 $\cup$ S2 $\cup$... ove per ogni i Si $\neq \varnothing$ e per ogni i, j, i $\neq$ j, si ha che:
#todo 
- [ ] da scrivere definizione in latex e sistemare le altre espressioni
Le varie Si sono dette classi di equivalenza. 
Se a appartiene ad Si allora con la notazione [a]_R si denota la classe Si. 
Se S è partizionato in un numero finito di classi S1 unito S2 unito ... unito Sk allora R si dice di indice finito (k) su S. 
Date due relazioni di equivalenza R1 e R2 sullo stesso insieme S, R1 è un raffinamento di R2 se ogni classe di equivalenza della partizione indotta da R1 è sottoinsieme di qualche classe di equivalenza della partizione indotta da R2.

Esempi:
![[myhill_nerode_esempio.png]]

#todo
- [ ] da aggiungere Lemma 5.16 e Teorema 5.17 con le relative dimostrazioni

### In altre parole...
Il <mark style="background: #BBFABBA6;">teorema di Myhill-Nerode</mark> afferma che un linguaggio formale è regolare se e solo se il numero di classi di equivalenza su tutte le stringhe del linguaggio è finito.

Le <mark style="background: #ABF7F7A6;">classi di equivalenza</mark> sono insiemi di stringhe che sono indistinguibili rispetto al linguaggio formale. In altre parole, due stringhe appartengono alla stessa classe di equivalenza se e solo se il linguaggio accetta entrambe le stringhe o le rifiuta entrambe. Le classi di equivalenza sono importanti perché, per esempio, possono essere usate per rappresentare l'insieme di tutti i prefissi di una stringa.

<mark style="background: #FFB8EBA6;">L'indice finito</mark> di un linguaggio è il numero di classi di equivalenza su tutte le stringhe del linguaggio. Se l'indice finito è finito, allora il linguaggio è regolare.

Un <mark style="background: #FFB86CA6;">raffinamento</mark> è una suddivisione di una classe di equivalenza in sottoinsiemi più piccoli. Il processo di raffinamento viene utilizzato per ridurre l'indice di un linguaggio, ovvero il numero di classi di equivalenza, per dimostrare che il linguaggio è regolare. Il raffinamento può essere ottenuto applicando un insieme di relazioni di equivalenza su tutte le stringhe del linguaggio. Queste relazioni sono derivate dalle proprietà del linguaggio e dal comportamento dell'automa finito deterministico associato al linguaggio.

Le <mark style="background: #D2B3FFA6;">relazioni di equivalenza</mark> sono una forma di relazione binaria tra elementi di un insieme che soddisfa tre proprietà: riflessività, simmetria e transitività.
In altre parole, una relazione di equivalenza è una relazione che stabilisce l'equivalenza tra gli elementi di un insieme, in base a qualche criterio di somiglianza. Ad esempio, se consideriamo l'insieme dei numeri interi, la relazione di equivalenza "essere congruenti modulo 5" definisce una classe di equivalenza per ciascun residuo modulo 5.

[_Torna all'indice_](#proprietà%20dei%20linguaggi%20regolari)

---

## Minimizzazione di DFA
<mark style="background: #FFB86CA6;">L'algoritmo di minimizzazione di un DFA è un metodo per ottenere l'automa finito deterministico più piccolo equivalente ad un dato DFA.</mark> L'obiettivo è ridurre il numero di stati dell'automa, mantenendo l'equivalenza con l'automa originale.

L'algoritmo di minimizzazione di un DFA può essere diviso in due fasi principali: la prima fase è la suddivisione degli stati dell'automa in gruppi di equivalenza, mentre la seconda fase è la costruzione del nuovo DFA minimizzato utilizzando i gruppi di equivalenza.

> I *gruppi di equivalenza* sono un insieme di stati di un automa finito che sono equivalenti rispetto ad un certo criterio di equivalenza. 
> Nello specifico, in un DFA due stati sono equivalenti se accettano o rifiutano lo stesso insieme di stringhe. Pertanto, i gruppi di equivalenza rappresentano una partizione degli stati dell'automa in sottoinsiemi che soddisfano questa proprietà di equivalenza.

Ecco i passi dell'algoritmo:
1. Inizialmente si suddividono gli stati del DFA in due gruppi: uno contenente gli stati finali e l'altro contenente gli stati non finali.
    
2. Si procede con la suddivisione dei gruppi in base alle transizioni del DFA. Per fare ciò, si considerano tutte le coppie di stati (p,q) che appartengono a due gruppi differenti, e si valuta se ci sono simboli di input che portano uno stato del primo gruppo in un altro stato del secondo gruppo, oppure viceversa. In tal caso, si separano i due stati e si creano due nuovi gruppi.
    
3. Si ripete il passo 2 finché non ci sono più nuove suddivisioni possibili. A questo punto, ogni gruppo contiene stati equivalenti, cioè stati che hanno lo stesso comportamento di accettazione/rifiuto delle stringhe.
    
4. Si costruisce un nuovo DFA utilizzando i gruppi di equivalenza come stati e le transizioni del DFA originale. In particolare, se l'automa originale ha una transizione da uno stato p ad uno stato q con un simbolo di input a, allora nel nuovo DFA si ha una transizione dal gruppo contenente p al gruppo contenente q, etichettata con il simbolo a.
    
5. Si seleziona uno stato rappresentante per ogni gruppo, in base alla definizione dell'automa originale. Ad esempio, se un gruppo contiene uno stato finale, allora lo stato rappresentante del gruppo deve essere un stato finale.
    
Il DFA ottenuto con questo algoritmo ha lo stesso comportamento dell'automa originale, ma con un numero minimo di stati.

Esempio:
![[minimizzazione_dfa_esempio.png]]

[_Torna all'indice_](#proprietà%20dei%20linguaggi%20regolari)