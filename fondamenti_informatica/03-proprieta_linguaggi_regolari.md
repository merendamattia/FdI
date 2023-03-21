# Proprietà dei linguaggi regolari
```toc
```
---
<mark style="background: #FFF3A3A6;">TODO: da aggiungere qualche esempio visto a lezione</mark>
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
![[linguaggio_non_regolare.png]]

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