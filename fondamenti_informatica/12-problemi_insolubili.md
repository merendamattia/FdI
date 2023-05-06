# Problemi insolubili
```toc
```
---

In questo Capitolo analizzeremo alcuni problemi classici non risolvibili nella teoria della effettiva calcolabilità sviluppata fino ad ora. Il più classico problema insolubile è il problema della terminazione posto da Turing.

Esiste una procedura effettiva tale che dati $x$ e $y$ determina se $φ_x(y)$ è definita o no?

---

## Lemma 15.1
$$
\text{Non esiste una funzione ricorsiva }g \text{ tale che per ogni }x:
$$
![[lemma15-1.png]]
![[dimostrazione_lemma15-1.png]]

[_Torna all'indice_](#problemi%20insolubili)

---

## Teorema 15.2
$$
\text{Non esiste una funzione ricorsiva }ψ \text{ tale che per ogni }x\; e \;y:
$$
Dimostrazione: Se esistesse allora esisterebbe un indice $x_0$ tale che $φ_{x_0} (x) = ψ(x, x)$. 
$ψ(x, x)$ non è altro che la funzione $g(x)$ dimostrata non esistere nel Lemma 15.1.

[_Torna all'indice_](#problemi%20insolubili)

---

## Teorema 15.3
$$
\text{Non esiste una funzione ricorsiva }f \text{ tale che per ogni }x:
$$
![[teorema15-3.png]]
![[dimostrazione_teorema15-3.png]]

[_Torna all'indice_](#problemi%20insolubili)
