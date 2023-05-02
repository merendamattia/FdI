# Tesi di Church-Turing
$$
\textit{La classe delle funzioni “intuitivamente calcolabili” coincide con la classe delle funzioni Turing calcolabili.}
$$

> Si tratta chiaramente di una tesi indimostrabile, vista l’impossibilità di maneggiare formalmente (= matematicamente) la nozione di “intuitivamente calcolabile”.

Accettando la Tesi di Church-Turing si osserva immediatamente la notevole importanza che assumono le funzioni calcolabili da MdT, o equivalentemente, le funzioni parziali ricorsive o λ-definibili. Queste classi di funzioni vengono a rappresentare la classe delle funzioni calcolabili effettivamente mediante un algoritmo. 

Questa Tesi permette di limitare l’estensione di ciò che è effettivamente calcolabile: se dimostriamo che una funzione non è parziale ricorsiva, allora, in virtù della Tesi di Church-Turing, essa non è calcolabile in nessun modo effettivo. Analogamente, dare un algoritmo per una funzione corrisponde a dimostrare, per la Tesi di Church-Turing, che essa è una funzione parziale ricorsiva.

> Questo utilizzo della Tesi di Church-Turing è <u>fondamentale</u>. Infatti, sarà sufficiente dimostrare la realizzabilità di un algoritmo per affermare l’esistenza di una MdT o di una funzione parziale ricorsiva corrispondente, senza dover es- ibire una tale macchina o una funzione per calcolarlo.

Questa caratteristica della Tesi di Church-Turing darà un aspetto apparentemente informale alle dimostrazioni di effettiva calcolabilità di funzioni.

Ogni volta che una funzione risulterà “palesemente” calcolabile, la si accetterà come effettivamente calcolabile da uno dei formalismi prescelti, senza dover costruire la MdT o altra funzione corrispondente. 

Concetti di calcolabilità:
- "effettiva" (ovvero associata all’esistenza di una MdT), 
- "algoritmica" (ovvero associata all’esistenza di un algoritmo che soddisfi i requisiti a–l),
- "ricorsiva" (ovvero associata ad una funzione ricorsiva parziale che la calcola).

A questo punto della trattazione, è bene distinguere, per chiarezza, tra due nozioni diverse di calcolabilità. Infatti è possibile definire una funzione g per cui sappiamo esistere un algoritmo ma per la quale non sappiamo dare l’algoritmo che la calcola.

Consideriamo le funzioni definite nel modo seguente:
![[calcolabilita_esempio.png]]

È chiaro che $g$ è calcolabile: dato un algoritmo che genera l’espansione decimale di $π$, g sarà o la funzione costante $g(x) = 1$, nel caso vi sia un numero arbitrariamente grande di occorrenze successive di '5' in $π$, che è chiaramente una funzione calcolabile.

Oppure sarà la funzione calcolata da un qualche algoritmo che, fissato un $k$ (ed esempio il massimo numero di '5' consecutivi in $π$), calcola:
![[calcolabilita_esempio2.png]]

In questo secondo caso esiste sicuramente un tale $k$ che permette di individuare l’algoritmo cercato, ma ci è impossibile sapere quale sia il $k$ giusto. In entrambi i casi la funzione g è calcolabile (ed è in particolare primitiva ricorsiva), ma in generale non sappiamo costruire effettivamente un algoritmo per calcolarla. 
Al contrario, per $f$ non siamo in grado a tutt'oggi di affermare nulla sulla sua calcolabilità effettiva. 

Pertanto, mentre per $g$ è possibile invocare la Tesi di Church-Turing, ed affermare che esiste una MdT che la calcola, anche se non si sa quale, per $f$ questo non è possibile. 
Accettando quindi di considerare calcolabile ogni funzione per la quale <u>esiste</u> un algoritmo che la calcoli, possiamo nel seguito utilizzare la Tesi di Church-Turing ogni qual volta sia chiara l’esistenza di un algoritmo per calcolare una data funzione.

[_Torna all'indice_](#Tesi%20di%20Church-Turing)