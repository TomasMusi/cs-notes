# Kombinatorika

V matematice používáme různé způsoby, jak spočítat kolik různých možností můžeme vytvořit při výběru věcí z nějaké množiny. Důležité je, zda na pořadí záleží nebo ne.

## 1. Variace (V)

### Co to je?

Variace znamenají, že při výběru záleží na pořadí.  
Tzn. pokud máš tři různé vědci a vybířáš z nich, pak různé uspořádání těchto věcí (pořadí) znamená různé možnosti.

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