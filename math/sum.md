# Sum

## Co je to suma?

Suma je způsob, jak zapsat **dlouhý součet čísel nebo výrazů** pomocí řeckého písmene sigma Σ

$$\sum_{i=1}^{n} a_i$$

To znamená:
- „Sečti všechny členy $a_i$ od $i=1$ do $i=n$.“

**Co znamenají jednotlivé části?**

- $\sum$ – řecké písmeno sigma, znamená „suma“ = součet.
- $i=1$ – **odkud začínám počítat** (spodní index). Tady od 1.
- $n$ – kde končím (horní index). Tady u čísla $n$.
- $a_i$ – obecný **člen součtu** (může to být číslo, výraz, mocnina, zlomek…).

### Co je to obecný člen $a_i$?

### 1) Nejjednodušší člen
Pokud $a_i = i$, pak suma znamená:

$$\sum_{i=1}^{5} i = 1 + 2 + 3 + 4 + 5$$

👉 obecný člen je jen „vezmi číslo $i$“.

### 2) Mocniny
Pokud $a_i = i^2$, pak:

$$\sum_{i=1}^{4} i^2 = 1^2 + 2^2 + 3^2 + 4^2$$

👉 obecný člen je „vezmi číslo $i$ a umocni ho na druhou“.

---

### 3) Zlomky
Pokud $a_i = \tfrac{1}{i}$, pak:

$$\sum_{i=1}^{4} \frac{1}{i} = \frac{1}{1} + \frac{1}{2} + \frac{1}{3} + \frac{1}{4}$$

👉 obecný člen je „vezmi převrácenou hodnotu čísla \(i\)“.

### Příklad 1

$$\sum_{i=1}^{5} i$$
= 1+2+3+4+5=15

### Příklad 2

$$\sum_{k=1}^{4} k^2$$

$$1^2 + 2^2 + 3^2 + 4^2 = 1 + 4 + 9 + 16 = 30$$


## Rychlé výpočty pomocí sumy

Díky sumě existují **vzorce**, které zkracují dlouhé sčítání.


### 1) Součet prvních $n$ přirozených čísel

$$\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$$

**Příklad:**  
$$\sum_{i=1}^{5} i = \frac{5 \cdot (5+1)}{2} = \frac{30}{2} = 15$$

### 2) Součet druhých mocnin

$$\sum_{i=1}^{n} i^2 = \frac{n(n+1)(2n+1)}{6}$$

**Příklad:**  
$$\sum_{i=1}^{4} i^2 = \frac{4 \cdot 5 \cdot 9}{6} = \frac{180}{6} = 30$$

### 3) Součet třetích mocnin

$$\sum_{i=1}^{n} i^3 = \left( \frac{n(n+1)}{2} \right)^2$$

**Příklad:**  
$$\sum_{i=1}^{3} i^3 = ( \tfrac{3 \cdot 4}{2} )^2 = 6^2 = 36$$