# Insiemi ricorsivi e ricorsivamente enumerabili
```toc
```
---

Consideriamo un insieme $I ⊆ \mathbb{N}$. Ci chiediamo se $I$ è costruibile in modo algoritmico, ovvero se è possibile generare gli elementi di $I$ mediante una funzione che sia effettivamente calcolabile.

## Definizione 17.1 (Ricorsivamente Enumerabile)
Un insieme $I ⊆ \mathbb{N}$ è detto <mark style="background: #FFB86CA6;">ricorsivamente enumerabile</mark> *(r.e.)* se esiste una funzione ricorsiva (parziale o totale) $ψ$ tale che $I = dom(ψ)$.
![[definizione17-1.png]]

Sia $A ∈$ RE. La funzione parziale:
![[funzione_parziale.png]]
è detta <mark style="background: #BBFABBA6;">funzione semicaratteristica</mark> dell’insieme $A$.

> È chiaro che $A = dom(ψ_A)$.

Inoltre, essendo per ipotesi $A$ r.e. , la verifica della condizione $x ∈ A$ è semidecidibile, ovvero se $y$ è tale che $A = W_y \;,\; x ∈ A \;sse\; φ_y(x) ↓$ . Pertanto abbiamo dimostrato che un insieme è detto r.e. sse ha una funzione semicaratteristica parziale ricorsiva.

[_Torna all'indice_](#Insiemi%20ricorsivi%20e%20ricorsivamente%20enumerabili)

---

## Definizione 17.2 (Insieme Ricorsivo)
Un insieme A è detto <mark style="background: #FFB86CA6;">ricorsivo</mark> se esiste una funzione ricorsiva (totale) $f_A$ tale che:
![[definizione17-2.png]]

Esisteranno dunque $\aleph_0$ insiemi r.e. di cui una parte di uguale cardinalità sarà ricorsiva. Si nota infatti subito della definizioni che $$ A \text{ ricorsivo} \implies A \in RE$$
Dato $A$ insieme ricorsivo, basta infatti definire la funzione parziale e chiaramente ricorsiva:
![[funzione_parziale_chiaramente_ricorsiva.png]]

[_Torna all'indice_](#Insiemi%20ricorsivi%20e%20ricorsivamente%20enumerabili)

---

### Esempio 17.3
I seguenti sono insiemi ricorsivi:
- L’insieme $\{0, 2, 4, 6, . . .\}$ dei numeri pari.
- $\mathbb{N} \;e\; \varnothing$
- Ogni insieme finito.
- Ogni insieme $A$ tale che $\overline{A}$ è finito.

[_Torna all'indice_](#Insiemi%20ricorsivi%20e%20ricorsivamente%20enumerabili)

---

## Teorema 17.5 (Teorema di Post)
$$
\text{Un insieme } A \text{ è ricorsivo se solo se }A \; e \; \overline{A} \text{ sono r.e.}
$$
![[dimostrazione_teorema17-5.png]]