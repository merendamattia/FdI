# Proprietà dei linguaggi liberi dal contesto
```toc
```
---

Per i linguaggi CF valgono delle proprietà simili a quelle viste per i [linguaggi regolari](obsidian://open?vault=Uni&file=FdI%2Ffondamenti_informatica%2F03-proprieta_linguaggi_regolari).

## Pumping lemma per i linguaggi CF
Il pumping lemma per i linguaggi CF afferma che per ogni linguaggio CF $L$ esiste un numero naturale $n$ tale che, se una stringa $z$ di $L$ ha una lunghezza maggiore o uguale a $n$, allora $z$ può essere suddivisa in cinque parti, `z = uvwxy`, soddisfacendo le seguenti condizioni:
1.  $|vx| ≥ 1$
2.  $|vwx| ≤ n$
3.  per ogni $i ≥ 0$, la stringa $uv^iwx^iy$ appartiene a $L$.

In altre parole, se una stringa del linguaggio CF ha una lunghezza sufficientemente grande, allora è possibile trovare una sottostringa "pompabile" all'interno di essa che, ripetuta qualsiasi numero di volte, porta ad una nuova stringa che non appartiene più al linguaggio.

Se una stringa $z$ non rispetta queste condizioni, allora non può essere generata dal linguaggio CF $L$. In questo modo, il pumping lemma può essere utilizzato per dimostrare che un certo linguaggio non è CF, poiché se esiste una stringa $z$ che non può essere pompata, allora il linguaggio $L$ non può essere generato da una grammatica CF.

### Dimostrazione
![[dimostrazione_pumping_lemma.jpeg]]![[dimostrazione_pumping_lemma_2.jpeg]]

[_Torna all'indice_](#Proprietà%20dei%20linguaggi%20liberi%20dal%20contesto)

---

### Esempio
![[FdI/fondamenti_informatica/data/images/proprieta_linguaggi_CF/esempio1.png]]![[FdI/fondamenti_informatica/data/images/proprieta_linguaggi_CF/esempio2.png]]

[_Torna all'indice_](#Proprietà%20dei%20linguaggi%20liberi%20dal%20contesto)