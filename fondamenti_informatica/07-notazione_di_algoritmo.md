# Notazione intuitiva di algoritmo
```toc
```
---

Un algoritmo definisce una funzione, ovvero una associazione 
$$
\{input\} \longrightarrow \{output\}
$$
Questa può essere rappresentata matematicamente come una funzione sui dati manipolati dall’algoritmo.

## Requisiti di un algoritmo
1. Un algoritmo è di lunghezza finita.
2. Esiste un agente di calcolo che porta avanti il calcolo eseguendo le istruzioni dell’algoritmo.
3. L’agente di calcolo ha a disposizione una memoria dove vengono immagazzinati i risultati intermedi del calcolo.
4. Il calcolo avviene per passi discreti.
5. Il calcolo non è probabilistico.
6. Non deve esserci alcun limite finito alla lunghezza dei dati di ingresso.
7. Non deve esserci alcun limite alla quantità di memoria disponibile.
8. Deve esserci un limite finito alla complessità delle istruzioni eseguibili dal dispositivo.
9. Sono ammesse esecuzioni con un numero di passi finito ma illimitato.
10. Sono ammesse esecuzioni con un numero di passi infinito (cioè non terminanti).

$\to$ Se ci fermassimo qui, gli algoritmi calcolerebbero solo funzioni totali (definite per ogni input).
$\to$ Ma qualunque formalismo che calcoli solo funzioni totali non le calcola tutte!
$\to$ Per assurdo, supponiamo che in un certo formalismo si possano calcolare tutte e sole le funzioni totali.
$\to$ Sia dunque $P_x$ l’$x$-esimo programma in questo formalismo e che $P_x$ calcoli la funzione $g_x$.
$g_x$ è totale, ma allora anche $h(x) = g_x(x) + 1$ lo è.
$\to$ Siccome il nostro formalismo calcola tutte le funzioni totali, avremo $h = g_{x_0}$.
$\to$ Ma allora possiamo scrivere
$$
g_{x_0} (x_0) = h(x_0) = g_{x_0} (x_0) + 1,\qquad \text{assurdo!}
$$

[_Torna all'indice_](#Notazione%20intuitiva%20di%20algoritmo)

## Approfondimento
<mark style="background: #BBFABBA6;">I punti 1-3</mark> hanno una ovvia interpretazione. 
<mark style="background: #BBFABBA6;">Il punto 4</mark> afferma che il calcolo non avviene mediante dispositivi analogici. 
<mark style="background: #BBFABBA6;">Il punto 5</mark> afferma che il calcolo non obbedisce a nessuna legge di probabilità. 

<mark style="background: #ABF7F7A6;">Il punto 6</mark> è ragionevole: ad esempio un algoritmo di somma deve poter funzionare per ogni possibile addendo, ovvero numero naturale, e per <mark style="background: #ABF7F7A6;">il punto 7</mark> è necessario un chiarimento. Per evidenziare la necessità di assumere una memoria illimitata facciano osservare che, limitandola, alcuni algoritmi noti per calcolare semplici funzioni non potrebbero funzionare. Ad esempio la funzione $λx. x^2$ non sarebbe calcolabile poichè lo spazio di memoria necessario per calcolare il quadrato di $x$ dipende da $x$, e per il punto 6, esso deve essere illimitato.

<mark style="background: #FFB8EBA6;">Il punto 8</mark>, in relazione al punto 1, stabilisce la intrinseca finitezza del dispositivo di calcolo. 
Ad esempio, pensando ad un calcolatore, esso sarà in grado di calcolare solo indirizzando direttamente una parte finita della sua memoria (registri o memoria RAM) stabilendo quindi un limite nella complessità delle istruzioni eseguibili. Un dispositivo di calcolo può effettivamente tenere traccia solo di un numero finito di simboli, ovvero esso può reagire (eseguendo un istruzione) tenendo conto di un numero finito di simboli ricordati. Questo venne intuitivamente giustificato da Turing che per primo analizzò formalmente il concetto di effettiva calcolabilità, con l’intrinseca limitazione della memoria umana. Tuttavia, non c’è limite alla memoria ausiliaria, come visto nel punto 7. 

Per quanto riguarda <mark style="background: #FFB86CA6;">il punto 9</mark>, osserviamo che non essendo limitabile il numero di passi richiesti per eseguire un generico algoritmo (si pensi alla moltiplicazione o alla funzione $λx. x^2$ discussa nel punto 7), non è possibile stabilire a priori un limite massimo sul numero di passi nell’esecuzione di un algoritmo.

<mark style="background: #D2B3FFA6;">Il punto 10</mark> rappresenta una necessità intrinseca, e come abbiamo visto irrinunciabile, nella trattazione matematica di ciò che è effettivamente calcolabile. Secondo questa ipotesi, la funzione $h$ descritta in precedenza può risultare indefinita su alcuni argomenti (ad esempio $x_0$), ovvero indicando con $↑$ il simbolo di indefinito, la precedente uguaglianza può risultare valida (non contraddittoria):
$$
↑\; = g_{x_0} (x_0) = h(x_0) = g_{x_0} (x_0) + 1 =\; ↑
$$

[_Torna all'indice_](#Notazione%20intuitiva%20di%20algoritmo)