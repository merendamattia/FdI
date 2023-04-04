# Automi a pila
```toc
```
---

#todo 
- [ ] Da terminare

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

### Esempio
![[esempio.png]]

[_Torna all'indice_](#automi%20a%20pila)

---