# Logaritmy

## 1. Základy mocnin (exponentů)

Musíš chápat:
- Co je mocnina

aⁿ = a · a · ... · a (n-krát)

3⁴  
- 3 = základ  
- 4 = exponent (mocnitel) říká, kolikrát násobíme  

## 2. Pravidla mocnin

### 1. Když násobíš dvě stejné základy:

$a^{m} \cdot a^{n} = a^{m+n}$

Když máš:  

$2^{3} \cdot 2^{4} → (2 \cdot 2 \cdot 2) \cdot (2 \cdot 2 \cdot 2 \cdot 2)$  

To je 7 dvojek = $2^{7}$  

$2^{3} \cdot 2^{4} = 2^{3+4} = 2^{7}$

**Sečteš exponenty**

### 2. Když dělíš dvě stejné základy:

$\frac{aᵐ}{aⁿ}$ = aᵐ⁻ⁿ

Například:

$\frac{2⁵}{2²}$ = $\frac{(2·2·2·2·2)}{(2·2)}$  = 2³

$\frac{2⁵}{2²}$ = 2⁵⁻² = 2³

**Odečteš exponenty**

### 3. Když mocníš mocninu:

(aᵐ)ⁿ = aᵐ·ⁿ

Například:

$(2^{3})^{2} = (2^{3}) \cdot (2^{3}) = 2^{3+3} = 2^{6}$  
nebo  
$(2^{3})^{2} = 2^{3 \cdot 2} = 2^{6}$

**Vynásobíš exponenty**

### 4. Každé číslo na nultou = 1:

a⁰ = 1

### 5. Záporný exponent znamená „obráceně“:

$a^{-n}$ = $\frac{1}{aⁿ}$

Například:

$2^{-3}$ = $\frac{1}{2³}$ = $\frac{1}{8}$


# Logaritmus

Co je logaritmus?
Na kolikrát musím umocnit základ, abych dostal určité číslo.

Například:
- $2^{1} = 2$
- $2^{2} = 4$
- $2^{3} = 8$

$\log_{2}(8) = 3$

Na kolikrát musím umocnit číslo b, abych dostal a?

$\log_{b}(a) = x$

- b = základ logaritmu (číslo, které umocňuješ.)
- a = výsledek (co chceš dostat) 
- x = exponent (odpověď, kterou hledáš)

**Logaritmus je inverzní operace k mocnině**

## Příklady

- $\log_{2}(8) = 3$
- $\log_{10}(1000) = 3$
- $\log_{2}(64) = 6$
- $\log_{5}(1) = 0$
- $\log_{4}(64) = 3$

Na desetinný výsledek: 
- $\log_{10}(2) \approx 0.30$
- $\log_{2}(10) \approx 3.32$


s úpravami.

- $\log_{2}(4 \cdot 8) = \log_{2}(32) = 5$
- $\log_{3}\\left(\tfrac{81}{9}\right) = \log_{3}(9) = 2$
- $\log_{5}(25^{3}) = 3$, protože $\log_{5}(25) = 2 → 2 \cdot 3 = 6$


# Logaritmická pravidla

### 1. Součin (násobení)

$\log_{b}(x \cdot y) = \log_{b}(x) + \log_{b}(y)$

Například:  
$\log_{2}(4 \cdot 8) = \log_{2}(4) + \log_{2}(8) = 2 + 3 = 5$

---

### 2. Podíl (dělení)

$\log_{b}\\left(\tfrac{x}{y}\right) = \log_{b}(x) - \log_{b}(y)$

Například:  
$\log_{2}\\left(\tfrac{8}{2}\right) = \log_{2}(8) - \log_{2}(2) = 3 - 1 = 2$


### 3. Mocnina

$\log_{b}(x^{n}) = n \cdot \log_{b}(x)$


$\log_{2}(8^{2}) = 2 \cdot \log_{2}(8) = 2 \cdot 3 = 6$

### 4. Změna základu

$\log_{a}(x) = \frac{\log_{b}(x)}{\log_{b}(a)}$

Například:

$\log_{2}(10) = \frac{\log_{10}(10)}{\log_{10}(2)} = \frac{1}{0.30} \approx 3.32$

Dobrý využít, když máš kalkulačku, která umí jen log $log_{10}$.

### Poznámka
Logaritmické Funkce jsou jako stroj, kam dáváš čísla a on ti vrací jiné číslo. Graf je kreslený záznam toho, co ten stroj dělá.
