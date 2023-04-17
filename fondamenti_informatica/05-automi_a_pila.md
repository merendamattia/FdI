# Automi a pila
```toc
```
---

## Che cosa sono?
Gli <mark style="background: #FFB86CA6;">automi a pila</mark> sono un tipo di automi a stati finiti estesi, ovvero una classe di macchine che rappresentano una classe di linguaggi formali. 
In particolare, gli automi a pila utilizzano una pila (struttura dati LIFO) per effettuare delle operazioni di memorizzazione e recupero di simboli durante il riconoscimento di una stringa.

Un automa a pila è una macchina costituita da un controllo che è un automa a stati finiti, un nastro di input che è di sola lettura (come negli NFA e DFA), ed una pila sulla quale sono possibili le operazioni di: `push(X)`, `pop(X)`, `empty`:
- L’istruzione `push(X)` sposta una stringa X in testa alla pila,  
- l’istruzione `pop(X)` preleva il simbolo in testa alla pila, e  
- l’istruzione `empty` verifica, restituendo valore booleano, se la pila è vuota o meno.

![[architettura.png]]

[_Torna all'indice_](#automi%20a%20pila)

## Azioni di un automa a pila
Le azioni possibili di un automa a pila sono:
- Leggere dal nastro e dalla pila (`pop`) contemporaneamente 
	- avanzare la testina a destra sul nastro  
	- cambiare stato nel controllo  
	- inserire una stringa (anche vuota) sulla pila (`push`)
- Leggere solo dalla pila (`pop`)  
	- cambiare stato nel controllo  
	- inserire una stringa (anche vuota) sulla pila (`push`)

[_Torna all'indice_](#automi%20a%20pila)

---

## Automa a pila non deterministico (APND)
![[definizione.png]]
dove $\varphi_f(Q × R^*)$ è l'insieme delle parti dell'insieme di coppie di stati e simboli dello stack.

In pratica, la funzione di transizione descrive come l'automa deve comportarsi quando incontra un simbolo di input o un simbolo dallo stack, decidendo in base alla coppia (stato corrente, simbolo di input/simbolo dallo stack) in quale stato andare e quale simbolo da aggiungere o rimuovere dallo stack.

Gli automi a pila sono utilizzati per riconoscere i linguaggi che non possono essere riconosciuti dagli automi a stati finiti, come ad esempio i linguaggi context-free. In particolare, gli automi a pila sono in grado di riconoscere i linguaggi context-free perché la pila consente loro di "ricordare" l'ordine in cui i simboli non terminali sono stati generati.

Una <mark style="background: #FFB8EBA6;">descrizione istantanea</mark> di un automa a pila è una descrizione completa del suo stato in un dato momento. Essa consiste di tre parti: lo stato corrente dell'automa, la parte del nastro che è stata già letta e lo stato corrente della pila.

> Una descrizione istantanea rappresenta una "fotografia" dello stato (stato + nastro + pila) della macchina ad un certo istante.

Se $(p, γ) ∈ δ(q, a, Z)$ allora è definito un <mark style="background: #ABF7F7A6;">passo di derivazione</mark> dell’APND:
$$(q,aw,Zα)→M (p,w,γα)$$

Il <mark style="background: #BBFABBA6;">linguaggio riconosciuto</mark> da un APND è l'insieme di tutte le stringhe che possono essere accettate partendo dallo stato iniziale dell'automa e seguendo una sequenza di passi di derivazione. L'automa accetta una stringa se c'è almeno una sequenza di passi di derivazione che porta ad uno stato finale.

Il linguaggio riconosciuto si può definire in due modi diversi: il linguaggio di accettazione per stato finale $L_f(M)$ e il linguaggio di accettazione per pila vuota $L_p(M)$.

![[linguaggi.png]]

In altre parole, $L_f$ rappresenta il linguaggio delle stringhe che portano l'automa a riconoscere l'input facendo una transizione in uno stato finale, mentre $L_p$ rappresenta il linguaggio delle stringhe che portano l'automa a riconoscere l'input svuotando la pila.

[_Torna all'indice_](#automi%20a%20pila)

---

### Proposizione 7.3
$$
\text{Per ogni APND } M, \text{ esiste un APND } M' \text{ tale che } L_f(M) = L_p(M')\cdot
$$
<mark style="background: #BBFABBA6;">Significa che</mark> per ogni automa a pila non deterministico $M$, è possibile costruire un altro automa a pila non deterministico $M'$ tale che il linguaggio riconosciuto da $M'$ ($L_f(M')$) sia uguale al linguaggio riconosciuto da $M$ ($L_p(M)$). In altre parole, le due definizioni di linguaggio accettato da un APND ($L_p$ e $L_f$) sono equivalenti.

La dimostrazione di questa proposizione consiste nell'osservare che ogni APND $M$ può essere trasformato in un altro APND $M'$ che accetta lo stesso linguaggio di $M$, ma con la restrizione che la pila di $M'$ sia sempre vuota quando $M'$ accetta. Questa trasformazione può essere ottenuta sostituendo le epsilon-transizioni di $M$ con transizioni che "puliscano" la pila, ovvero che rimuovano uno o più simboli dalla pila fino a renderla vuota. In questo modo, l'APND $M'$ accetta solo se raggiunge uno stato finale con la pila vuota, cioè quando ha consumato tutti i simboli di input e ha svuotato la pila.

Quindi, se un APND $M$ accetta un certo linguaggio $L$, allora possiamo costruire un altro APND $M'$ che accetta lo stesso linguaggio $L$, ma che ha la proprietà aggiuntiva che la pila sia vuota quando accetta. In questo modo, $Lf(M) = Lp(M')$. Poiché questa costruzione vale per qualsiasi APND $M$, la proposizione è dimostrata.

[_Torna all'indice_](#automi%20a%20pila)

---

### Esempi
![[esempio1.png]]

![[esempio2.png]]

[_Torna all'indice_](#automi%20a%20pila)

---

### Lemma 7.7
$$
\text{Se } L = Lp(M) \text{ con } M \text{ APND, allora }L = Lp(M′) \text{ con } M' \text{ APND con 1 solo stato.}
$$
Il lemma afferma che per un linguaggio $L$ riconosciuto da un automa a pila non deterministico (APND) $M$, esiste un altro APND $M'$ con un solo stato tale che riconosca lo stesso linguaggio, ovvero $L_p(M) = L_p(M')$. In altre parole, <mark style="background: #ABF7F7A6;">ogni linguaggio riconosciuto da un APND può essere riconosciuto da un APND con un solo stato.</mark>

La dimostrazione del lemma si basa sull'idea di simulazione dell'APND $M$ con un APND $M'$ con un solo stato. In particolare, l'APND $M'$ simula tutte le possibili computazioni dell'APND $M$ su una data stringa di input, tenendo traccia della posizione del testo di input e dello stato della pila. Questa simulazione può essere realizzata utilizzando la tecnica dell'[unfolding](obsidian://open?vault=Uni&file=FdI%2Ffondamenti_informatica%2F04-grammatiche_libere_dal_contesto), che genera un numero finito di stati e transizioni equivalenti a tutte le possibili computazioni dell'APND $M$ su una data stringa di input.

Quindi, il lemma implica che ogni linguaggio riconosciuto da un APND può essere riconosciuto da un APND con un numero finito di stati, il che semplifica notevolmente la costruzione di automi a pila per i linguaggi non regolari.

[_Torna all'indice_](#automi%20a%20pila)

---

### Teorema di Chomsky-Schützenberger (teorema 7.8)
$$
\text{Se } L = L_p(M) \text{ con } M \text{ APND con 1 stato, allora L è CF.}
$$
<mark style="background: #FFB86CA6;">Esso afferma che</mark> se un linguaggio $L$ è riconosciuto da un automa a pila non deterministico $M$ avente un solo stato, allora $L$ è un linguaggio generato da una grammatica context-free. In altre parole, se un linguaggio è riconoscibile da un APND con un solo stato, allora è possibile costruire una grammatica CF che genera lo stesso linguaggio.

La dimostrazione di questo teorema si basa sull'idea di trasformare l'APND $M$ in una grammatica CF $G$ equivalente. La chiave di questa trasformazione è l'osservazione che le computazioni dell'APND $M$ su una stringa di input possono essere viste come alberi di derivazione di una grammatica CF. In particolare, ogni cammino attraverso la pila di $M$ corrisponde a una derivazione nella grammatica CF.

La costruzione di $G$ a partire da $M$ avviene in due fasi:
1. Si costruisce una grammatica $G$' in cui ogni simbolo non terminale $A$ di $G$' rappresenta una configurazione della pila di $M$, ovvero una tripla $(q, w, γ)$, dove $q$ è lo stato corrente di $M$, $w$ è il prefisso della stringa di input che è stata letta finora e $γ$ è il contenuto attuale della pila di $M$. Le produzioni di $G$' descrivono come la pila di $M$ si evolve da una configurazione all'altra durante una computazione.
2. Si costruisce una nuova grammatica $G$ a partire da $G$' eliminando i simboli non utilizzati. La grammatica risultante $G$ genera esattamente il linguaggio $L_p(M)$.

La costruzione di questa grammatica CF $G$ dimostra che ogni linguaggio riconosciuto da un APND con un solo stato è un linguaggio context-free.

#### Esempio
![[esempio3.png]]
![[esempio3_2.png]]

[_Torna all'indice_](#automi%20a%20pila)

---

### Teorema 7.10
$$
\text{Sia }L \text{ CF. Allora esiste un APND } M \text{ tale che }L = L_p(M).
$$
<mark style="background: #D2B3FFA6;">Il teorema afferma che per ogni linguaggio che può essere generato da una grammatica context-free (CF), esiste un automa a pila non deterministico (APND) che riconosce lo stesso linguaggio.</mark> In altre parole, ogni linguaggio CF può essere riconosciuto da un APND. Questo è un risultato importante perché dimostra che i due modelli di calcolo (grammatiche CF e automi a pila) sono equivalenti in termini di potenza espressiva. Ciò significa che un problema che può essere risolto con una grammatica CF può essere risolto anche con un APND, e viceversa.

[_Torna all'indice_](#automi%20a%20pila)