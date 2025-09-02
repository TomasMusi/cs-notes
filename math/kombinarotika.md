# Kombinatorika

V matematice používáme různé způsoby, jak spočítat kolik různých možností můžeme vytvořit při výběru věcí z nějaké množiny. Důležité je, zda na pořadí záleží nebo ne.

## 1. Variace (V)

### Co to je?

Variace znamenají, že při výběru záleží na pořadí.  
Tzn. pokud máš tři různé věci a vybířáš z nich, pak různé uspořádání těchto věcí (pořadí) znamená různé možnosti.

### Vzorec
$$
V(n,k) = \frac{n!}{(n-k)!}
$$

### Vysvětlení symbolů
- **$n$** – počet všech možných věcí, ze kterých vybíráme  
  (např. 3 různé barvy)  

- **$k$** – počet věcí, které chceme vybrat  
  (např. chceme 2 barvy)  

- **$n!$ (n faktoriál)** – součin všech celých čísel od 1 po $n$  
  (např. $4! = 4 \cdot 3 \cdot 2 \cdot 1 = 24$)  

- **$(n-k)!$** – to znamená, že z celkového počtu věcí $n$ vyloučíme $k$ vybraných a spočítáme faktoriál z těch, které zůstaly. Tento výraz ukazuje, že nás nezajimá pořadí zbylích.

### Příklad

Mějme 3 barvy: **červenou, modrou a zelenou**.  
Kolik způsobů je možné vybrat 2 barvy, pokud záleží na pořadí?

- $n = 3$ (barvy)  
- $k = 2$ (chceme vybrat 2 barvy)

$$
V(3,2) = \frac{3!}{(3-2)!} = \frac{3 \cdot 2 \cdot 1}{1!} = 6
$$

### Možnosti (výpis všech variací):
1. červená, modrá  
2. červená, zelená  
3. modrá, červená  
4. modrá, zelená  
5. zelená, červená  
6. zelená, modrá

## 2. Kombinace (C)

### Co to je?

Kombinace znamenají, že při výběru **nezáleží na pořadí**.  
Například pokud vyberu dvě barvy (**červenou a modrou**), je to stejné jako (**modrou a červenou**), protože pořadí není důležité.

### Vzorec
$$
C(n,k) = \frac{n!}{k! \cdot (n-k)!}
$$

### Příklad
Mějme 3 barvy: **červenou, modrou a zelenou**.  
Kolik způsobů je možné vybrat 2 barvy, když **nezáleží na jejich pořadí**?

- $n = 3$ (3 barvy)  
- $k = 2$ (chceme vybrat 2 barvy)

$$
C(3,2) = \frac{3!}{2! \cdot (3-2)!} = \frac{6}{2 \cdot 1} = 3
$$

### Možnosti (výpis všech kombinací):
1. červená, modrá  
2. červená, zelená  
3. zelená, modrá

## 3. Permutace (P)

### Co to je?

Permutace je způsob, jak spočítat, kolika způsoby můžeme poskládat všechny věci, které máme k dispozici, a záleží na pořadí.

### Vzorec
$$
P(n) = n!
$$

### Příklad
Mějme 3 písmena: **A, B, C**.  
Kolik způsobů je možné je uspořádat?

- $n = 3$ (3 prvky)

$$
P(3) = 3! = 3 \cdot 2 \cdot 1 = 6
$$

### Možnosti (výpis všech permutací):
1. ABC  
2. ACB  
3. BAC  
4. BCA  
5. CAB  
6. CBA

## Pravidlo součtu (pravidlo pro OR)

### Co to je?
Pravidlo součtu říká, že pokud máme dvě nebo více **nezávislých možností**, stačí je sečíst.

### Příklad

Mějme 3 nanuky (**čokoládový, jahodový a jablkový**)  
a 2 dorty (**čokoládový a ovocný**).  

Kolik možností máme, když si chceme vybrat **buď nanuk, nebo dort**?

- Počet možností pro nanuky = 3  
- Počet možností pro dorty = 2  

$$
3 + 2 = 5
$$

### Výsledek:
Celkem máme **5 možností**.

## Pravidlo součinu (pravidlo pro AND)

### Co to je?

Pravidlo součinu říká, že pokud máme několik **závislých možností** a chceme je kombinovat, musíme je **vynásobit**.

### Příklad
Mějme 3 trička (**červené, modré, zelené**)  
a 2 kalhoty (**džíny, sportovní**).  

Kolik možností máme, když chceme zvolit **kombinaci oblečení**?

- Počet možností pro trička = 3  
- Počet možností pro kalhoty = 2  

$$
3 \cdot 2 = 6
$$

Celkem máme **6 možností**.