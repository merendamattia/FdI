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

[Dimostrazione lemma 5.1 (Bar-Hillel, Perles, Shamir, 1961).](obsidian://open?vault=FdI&file=fondamenti_informatica%2Fdata%2Fpdf%2Fdim_lemma_5-1.pdf)

> Corollario 5.2: $n$ del Lemma 5.1 può essere preso come numero di stati del più piccolo automa riconoscente $L$.
> [Dimostrazione corollario 5.2.](obsidian://open?vault=FdI&file=fondamenti_informatica%2Fdata%2Fpdf%2Fdim_coroll_5-2.pdf)

Esempio:
![[linguaggio_non_regolare.png]]

[_Torna all'indice_](#proprietà%20dei%20linguaggi%20regolari)

---

## Proprietà di chiusura
Teorema 5.6. I linguaggi regolari sono chiusi rispetto alle operazioni di unione, concatenazione e chiusura di Kleene.

Teorema 5.7. I linguaggi regolari sono chiusi rispetto alla operazione di com- plementazione. Ovvero, se $L ⊆ Σ^*$ è regolare, anche $\overline{\rm L} = Σ^* \ L$ è regolare.

Corollario 5.8. I linguaggi regolari sono chiusi rispetto all’intersezione.

<mark style="background: #FFF3A3A6;">TODO: da approfondire</mark>