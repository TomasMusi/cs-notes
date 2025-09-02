# Matematická indukce

Matematická indukce je důkazová technika, kterou používáme k tomu, abychom prokázali, že nějaké tvrzení platí pro všechny přirozené čísla (tj. čísla 1,2,3,4...)

Je to způsob, jak dokázat nekonečně mnoho tvrzené, aniž bychom museli každé číslo zkoumat zvlášť.

## Indukce má 2 hlavní kroky:

### 1. Základní krok (ověření pro první číslo)

- Nejprve musíme dokázat, že tvrzení platí pro první číslo (obvykle $n=1$).  
- To je jako „nastartovat důkaz“ a ověřit, že první případ je správný.

### 2. Indukční krok (předpoklad pro $k \Rightarrow$ důkaz pro $k+1$)

- Pokud předpokládám, že tvrzení platí pro nějaké číslo $k$,  
  musím dokázat, že pak platí i pro číslo $k+1$.

Pokud byly oba kroky dokázány (základní + indukční krok),  
pak tvrzení platí pro **všechna přirozená čísla $n \geq 1$**.

### Příklad matematické indukce

Chceme dokázat, že platí:

$$
1 + 2 + 3 + \dots + n = \frac{n(n+1)}{2}
$$

To znamená, že když sečteme všechna čísla od 1 do $n$,  
dostaneme výsledek podle vzorce $\frac{n(n+1)}{2}$.

## 1. Základní krok

Zkontrolujeme, že tvrzení platí pro $n = 1$:

$$
1 = \frac{1 \cdot (1+1)}{2}
$$

$$
1 = \frac{1 \cdot 2}{2}
$$

$$
1 = 1
$$

Tvrzení tedy platí (neboť obě strany rovnice dávají stejné číslo.) pro $n = 1$.

## 2. Indukční krok

Teď předpokládejme, že tvrzení platí pro nějaké $k$.  
To znamená, že indukční předpoklad je:

$$
1 + 2 + 3 + \dots + k = \frac{k(k+1)}{2}
$$

Nyní chceme dokázat, že platí i pro $k+1$:

$$
1 + 2 + 3 + \dots + k + (k+1) = \frac{(k+1)(k+2)}{2}
$$

Začneme z indukčního předpokladu a přičteme $(k+1)$ na obě strany:

$$
1 + 2 + 3 + \dots + k + (k+1) 
= \frac{k(k+1)}{2} + (k+1)
$$

Upravíme pravou stranu na společný jmenovatel:

$$
\frac{k(k+1)}{2} + (k+1) 
= \frac{k(k+1)}{2} + \frac{2(k+1)}{2}
$$

$$
= \frac{k(k+1) + 2(k+1)}{2}
$$

$$
= \frac{(k+1)(k+2)}{2}
$$

Tím jsme dokázali, že když tvrzení platí pro $k$,  
platí i pro $k+1$.
