# Aritmetizzazione e universalità
```toc
```
---

Aritmetizzazione significa semplicemente traduzione nel linguaggio dell’aritmetica.

Il primo utilizzo dell’aritmetizzazione è dovuto a G ̈odel nel 1931 nella dimostrazione del risultato fondamentale di incompletezza dell’aritmetica; da qui anche il termine equivalente di Godelizzazione. Nel seguito considereremo le MdT come esempio ed applicheremo alle MdT il concetto di aritmetizzazione. 
Per la Tesi di Church-Turing, sappiamo che questa non è una restrizione, ed analoghe aritmetizzazioni possono essere definite per ogni sistema formale equivalente alle MdT.

## Enumerazione delle MdT
Sia $Σ = \{\$, 0\}$. Quante sono le macchine di Turing ‘distinte’ descrivibili? Si supponga $Q = \{q_0\}$. 
Si tratterà di riempire la tabella
![[tabella.png]]
in tutti i modi (significativi) possibili, ossia ogni singola casella potrà essere
1. _vuota_ (si immagini di scrivere $\$\; \$\; \$$)
2. $q_0 \; \$ \; R$
3. $q_0 \; \$ \; L$
4. $q_0 \; 0 \; R$
5. $q_0 \; 0 \; L$

Dunque ci sono <u>esattamente</u> $25 = 5 × 5$ macchine di Turing distinte ad un solo stato.

> Si può pensare a questo punto di definire un ordinamento $\triangleleft$ sulle macchine di Turing ad uno stato definibili.

Fissato un ordinamento su $Σ$ (poniamo $\$ <_Σ 0$), sia inoltre $L <_M R$ e si consideri la cella a sinistra più importante di quella a destra, essendo $M$ insieme dei possibili movimenti della testina, cioè $M = \{L, R\}$.
Si assuma che $\$\; \$\; \$$ sia minore di qualunque terna $q_0 \;s\; m$, allora si avrà
![[minimo.png]]

Più in generale, sia $Q = \{q0,...,q_{n−1}\}, \;Σ = \{s0 = \$,s1 = 0\}, \;m_0 = L, \;m_1 = R$.
Si definisca inoltre un ordinamento tra le $2 · n$ celle presenti (per righe, colonne, a zig zag etc.). Definendo esplicitamente l’ordinamento per ogni cella nel modo seguente:
![[definizione.png]]
si ha un buon ordine sull’insieme delle macchine di Turing aventi n stati, che sono in tutto
$$
(n·2·2+1)^{2n} = (4·n+1)^{2n}
$$
dunque ci saranno 25 MdT ad uno stato, 94 MdT a due stati, 136 MdT a tre stati, ...

$\to$ Si indica con $P_x$ la MdT di indice $x$ in una data (e fissata) aritmetizzazione.
$\to$ Si indica con $φ_x$ la funzione calcolata dalla macchina $P_x$.

[_Torna all'indice_](#Aritmetizzazione%20e%20universalità)

---

### Esempio
![[FdI/fondamenti_informatica/data/images/aritmetizzazione_e_universalita/esempio1.png]]

[_Torna all'indice_](#Aritmetizzazione%20e%20universalità)

---

### Teorema 14.2
$$
\text{Ci sono }\aleph_0 \;\text{macchine di Turing distinte o funzioni parziali ricorsive, e }\aleph_0 \;\text{funzioni ricorsive.}
$$
Dimostrazione: Segue banalmente dal fatto che tutte le funzioni costanti sono ricorsive. Pertanto ci sono almeno $\aleph_0$ funzioni ricorsive.

[_Torna all'indice_](#Aritmetizzazione%20e%20universalità)

---

### Teorema 14.3
$$
\text{Ci sono esattamente } \aleph_0 \;\text{funzioni calcolabili.}
$$
Dimostrazione: Segue dal teorema precedente per la Tesi di Church-Turing.

[_Torna all'indice_](#Aritmetizzazione%20e%20universalità)

---

### Teorema 14.4
$$
\text{Esistono funzioni (totali) } f : \mathbb{N} \to \mathbb{N} \text{ non Turing calcolabili.}
$$
![[dimostrazione_teorema14-4.png]]

[_Torna all'indice_](#Aritmetizzazione%20e%20universalità)

---

## Macchina di Turing Universale