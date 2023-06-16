```toc
```
---

## Automi

1. Se F è un linguaggio finito e L \ F è regolare, allora:
	- [v] L è regolare
	- [ ] L è finito
	- [ ] L = F
	- [ ] L è infinito
	- [ ] Nessuna delle altre
2. Un sottoinsieme di un linguaggio regolare è:
	- [v] Non decidibile
	- [ ] Decidibile
	- [ ] Nessuna delle altre
3. Quanti stati ha il DFA minimo che accetta il linguaggio su alfabeto {a,b,c} denotato dall'ER ((a+b)(a+b)...(a+b))* ? [(a+b) ripetuto n volte]
	- [v] nessuna
	- [ ] n + 2
	- [ ] n + 1
	- [ ] n
	- [ ] 2n
4. Il complemento di un linguaggio finito
	- [v] è regolare
	- [ ] è acontestuale non regolare
	- [ ] è irregolare
	- [ ] è finito
5. Un sottoinsieme di un linguaggio regolare è
	- [v] non decidibile
	- [ ] acontestuale
	- [ ] monotono
	- [ ] regolare
	- [ ] decidibile
6. Quali dei seguenti automi può accettare $(x \in \{0,1\}^* | n_O(x)=n_1(x) \}$ con nb($\epsilon$)=0 e nb(aw)=I - la-bl  + nb(w)
	- [v] APND
	- [ ] NFA
	- [ ] DFA
	- [ ] $\epsilon$-NFA
7. Quanti stati ha il DFA minimo che accetta il linguaggio su alfabeto {a,b,c} denotato dall'ER $\epsilon$ + (a+b)(a+b)...(a+b) ? [(a+b) ripetuto n volte]
	- [v] n + 2
	- [ ] n + 1
	- [ ] n
	- [ ] 2n
8. Quale dei seguenti automi si arresta sempre dopo aver effettuato un numero finitodi transizioni se riceve ni input una sequenza finita disimboli (non blank per la MdT) ?
	- [v] DFA
	- [ ] MdT
	- [ ] APND
	- [ ] APD

---

## Espressioni regolari
1. Quale tra le seguenti entità tra espressioni regolari <u>non</u> è valida?
	- [v] $(r^* + s^*) = r^* + s^*$
	- [ ] $ε =$ φ
	- [ ] $(r^* + s^*) = (r^*s^*)^*$
	- [ ] $(rs)^*r = r(sr)^*$
	- [ ] $(ε+r^*r)=r^*$
2. Quali delle seguenti espressioni regolari è tale che il linguaggio denotato non contiene stringhe con due 1 consecutivi?
	- [v] $(\epsilon + 1)(01+0)^*$
	- [ ] $(\epsilon + 1)(01+0)^*0$
3. L'espressione regolare $\varnothing a^* + \varnothing^*$ denota il linguaggio:
	- [v] $\{\epsilon\}$
	- [ ] $\{a\}^*$
	- [ ] $\{\epsilon, a\}$
	- [ ] $\{\varnothing\}$
	- [ ] Nessuna delle precedenti
4. Quale delle seguenti identità tra E.R. non è valida:
	- [v] nessuna
	- [ ] $ε^* =$ φ$^*$
	- [ ] $(r^* + s^*) = (r^*s^*)^*$
	- [ ] $(rs)^*r = r(sr)^*$
	- [ ] $(ε+r^*r)=r^*$
5. Quale delle seguenti identità traespressioni regolari non è valida:
	- [v] $(rs +r)^*rs = (rr^*s)^*$
	- [ ] $ε^* =$ φ$^*$
	- [ ] $(r^* + s^*)^* = (r^*s^*)$
	- [ ] $(rs)^*r = r(sr)^*$
	- [ ] $(ε+r^*r)=r^*$
6. Quale delle seguenti identità tra espressioni regolari non è valida:
	- [v] $s(rs +s)^*r = rr^*s(rr^*s)^*$
	- [ ] $(ε^*$ + φ)$^*$ = φ$^*$
	- [ ] $(s^*r)^*s^* = (r^*s)^*r^**$
	- [ ] $(rs)^*r = r(sr)^*$

7. Quale delle seguenti espressioni regolari su E = (a,b,c) denota il linguaggio {$\epsilon$} U {w $\in$ E* | il numero di occorrenze di a in w è pari e positivo}
	- [v] $((b+c)^*a(b+c)^*a(b+c)^*)^*$

8. Si considerino el espressioni regolari sull'alfabeto E = {0,1}
		r1 = $(0+1)^*(0011+1010)(0+1)^*$
		r2 = $\epsilon + (0+10+110)^*(\epsilon+1+11)$
	- [v] nessuna
9. Quale delle seguenti espressioni regolari sull'alfabeto E ={0,1} il linguaggio delle stringhe che contengono un numero'0' divisibili per 3?
	- [v] $(1^*01^*01^*01^*)^*+1^*$
10. Quale delle seguenti espressioni regolari su E = (a,b,c) denotail linguaggio {w $\in$ {a,b,c}* | il numero di occorrenze di a in w è dispari }
	- [v] $(b+c)^*a(b+c)^*a)^*((b+c)^*a(b+c)^*)$
11. Quali delle seguenti espressioni regolari è tale che il linguaggio denotato non contiene stringhe con due 1 consecutivi
	- [v] $(1+\epsilon)(01+0)^*$


---

## Grammatiche libere dal contesto
1. Un sottoinsieme di un linguaggio acontestuale
	- [v] nessuna ( non è decidibile )
	- [ ] è decidibile
	- [ ] è monotono
	- [ ] è regolare
	- [ ] è acontestuale
2. Qual è la cardinalità dell'insieme dei linguaggi acontestuali su di un alfabeto di n>0 simboli
	- [v] |N|
	- [ ] |P(N)|
	- [ ] 2^2^n
	- [ ] 2^n
3. Si considerino le seguenti grammatiche espresse in forma coincisa e si dica quale di queste è ambigua o se nessuna lo è:
	- [v] S -> SS | a
	- [ ] S -> aS | a
	- [v] S -> SaS | $\epsilon$
	- [ ] S -> aSa | $\epsilon$
4. La chiusura di Kleene di un linguaggio acontestuale
	- [v] è infinita
	- [ ] è monotona non acontestuale
	- [ ] è regolare
	- [ ] è acontestuale

---

## Macchine di Turing
1. Qual è la cardinalità dell'insieme delle MdT con n stati e m simboli?
	- [v] (2nm + 1)^2n
	- [ ] m^n
	- [ ] |P(n)|
	- [ ] |m|
	- [ ] nessuna
2. Identificare le eventuali affermazioni vere tra le seguenti, che riguardano l'uso delle MdT come riconoscitori di linguaggi formali
	- [v] nessuna delle altre
	- [ ] una MdT è più potente di un epsilon-NFA perchè il controllo della MdT non è a stati finiti
	- [ ] un epsilon-NFA ++ che potesse riavvolgere il nastro (di input) sarebbe tanto potente quanto una MdT
	- [ ] una MdT che muove la testina solo a dx è tanto potente quanto un epsilon-NFA

---

## Aritmetizzazione e universalità
1. La cardinalità delle funzioni parziali è:
	- [v] $|\wp(N)|$
	- [ ] $|N|$
	- [ ] Nessuna delle altre

---

## Insiemi ricorsivi e ricorsivamente enumerabili
1. Gli insiemi ricorsivamente enumerabili non sono chiusi rispetto
	- [v] Differenza
	- [ ] Intersezione
	- [ ] Unione
	- [ ] Nessuna delle altre

---

## Generale
1. Quali delle seguenti coppie hanno diverso peso espressivo:
	- [v] APD e APND
	- [ ] DFA e NFA
	- [ ] MdT ordinate e MdT con più nastri
	- [ ] ER ordinarie ed ER senza $\epsilon$
2. L'affermazione "Se I $\in$ N è un insieme X e I' = N \ I allora anche l' è X" se al posto di X scrivo:
	- [v] ricorsivo
	- [ ] ricorsivamente enumerabile
	- [ ] non ricorsivamente enumerabile
	- [ ] ricorsivamente enumerabile non ricorsivo
3. Quante sono le sottostringhe di una stringa di lunghezza n su di un alfabetodi m>0 simboli?
	- [v] 1 + n(n+1)/2
	- [ ] n(n+1)/2
	- [ ] m*n
	- [ ] m(m+1)/2
	- [ ] 1 + m(n+1)/2
4. Qual è la cardinalità dell'insieme delle stringhe lunghe n sull'alfabeto E?
	- [v] |E|^n
	- [ ] |P(N)|
	- [ ] n^|E|
	- [ ] 2^n
	- [ ] |N|
5. Qual è la cardinalità delle funzioni totali
	- [v] |P(N)|
6. Quale è la cardinalità degli insiemi <u>non</u> acontsestuali
	- [v] |P(N)|
7. Quali fra iseguenti problemi sono decidibili
		(a) Se l'intersezione di due linguaggi regolari è infinita 
		(b) Se una data grammatica è ambigua 
		(c) Se due APND accettano lo stesso linguaggio 
		(d) Se una grammatica è acontestuale
	- [v] (a) e (d)