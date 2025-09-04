# Funkce

**Definice**
Funkce je pravidlo, které každému prvku z množiny vstupů (*definiční obor*) přiřadí výstup z jiné množiny (*obor hodnot*)

### Vztah
- Každé $x$ může mít jen jedno $y$.
- Funkce je jako „stroj“ nebo „automat“ – vložíš hodnotu (např. 5), dostaneš výsledek (např. 10).

## Definiční Obor
Definiční obor je množina všech čísel, která smíš vložit do funkce. (Jaká X můžeme dosadit do funkce, aby to dávalo smysl.)

### Příklady

1. $f(x) = x^2$  
   - Definiční obor: $D(f) = \mathbb{R}$  
   - (můžeš dosadit libovolné reálné číslo)

2. $f(x) = \tfrac{1}{x}$  
   - Definiční obor: $D(f) = \mathbb{R} \setminus \{0\}$  
   - (můžeš dosadit všechna reálná čísla kromě nuly)

## Obor Hodnot

Obor hodnot je množina všech čísel. které z funkce můžou vypadnout jako výstup(y). Co vše mohu z funkce získat.

### Příklad

$f(x) = x^2$

- **Definiční obor:**  
  $D(f) = \mathbb{R}$  

- **Obor hodnot:**  
  $H(f) = \{ y \in \mathbb{R} \mid y \geq 0 \}$  

(tato funkce nikdy nemůže vrátit číslo menší než nula)

# Typy funkcí (Vlastnosti zobrazení)

## 1. Injekce (jednoznačné zobrazení)

Každý výsledek ($y$) přísluší **maximálně** jednomu $x$.

- žádné dvě různé hodnoty $x$ nesmí vést na stejný výsledek $y$

**Přirovnání:**  
Každý student má **jedinečný e-mail**.  
(Ale ne každý e-mail musí patřit studentovi.)

## 2. Surjekce (zobrazení „na“)

Schéma:  
$f : A \to B$

- $A$ je množina všech možných vstupů → **definiční obor**  
- $B$ je množina všech možných výstupů → **obor hodnot**

### Definice
Ve **surjekci** funkce přiřazuje tak, aby každý prvek z $B$ byl alespoň jednou dosažený z nějakého prvku v $A$.  

Formálně:  
$$
\forall y \in B \;\exists x \in A : f(x) = y
$$

**Slovy:**  
„Pro každý prvek z množiny B existuje nějaký vstup z A, který ho tvoří.“

### Příklad
- Množina $B = \{\text{HR}, \text{IT}, \text{Finance}\}$  
  Každé oddělení je ,,obsazené" -  

- Pokud by třeba žádný zaměstnanec nebyl v „IT“,  
  pak by v množině $B$ zůstal nepokrytý prvek → funkce **není surjekce**.

Surjekce = "S" jako "Satured" (vše v $B$ je nasyceno.)

## 3. Bijekce (obostranně jednoznačné)

Bijekce je **ideální / perfektní funkce**:  
- Každý vstup x má právě jedno výstupní y, a zároveň každé y má právě je dno x, které ho vytvořilo.

Bijekce = Injekce $\land$ Surjekce

### Přirovnání
- Studenti = množina $A$  
- Karty do jídelny = množina $B$  

Bijekce = každý student má jednu unikátní kartu a žádná nezbyla.

- Každý student má právě jednu kartu
- Každá karta patří přávě jednomu studentovi.

# Shrnutí

| Typ funkce | Co to znamená | Příklad |
|------------|----------------|---------|
| **Injekce** | $Y$ není sdíleno - každý výstup patří max. jednomu $X$ | Každý student má unikátní e-mail |
| **Surjekce** | každý výstup je pokryt, ale může ho mít více $X$ | Všechna oddělení mají zaměstnance |
| **Bijekce** | každý $X$ má právě jedno $Y$ a naopak | Každý student má jednu kartu a žádná karta nezbyde |


# Typy funkcí (druhy funkcí podle tvaru předpisu)

## 1. Konstantní funkce

- Předpis:  
  $y = c$
  kde $c$ je nějaké číslo (např. $y = 4$).
- Graf je **vodorovná čára**.
- Nezáleží, co dosadíš za $x$, vždy dostaneš stejný výsledek.

## 2. Lineární funkce

- Předpis:  
  $y = ax + b$
  kde $a$ a $b$ jsou čísla.
  - $a$ se říká **směrnice** – určuje, jestli graf roste nebo klesá.
  - $b$ je **posun na ose y** – místo, kde graf protíná osu $y$.

**Příklad:**  
$y = 3x + 5$

- $a = 3$ → funkce **roste** (čím větší číslo u $x$, tím rychleji roste).  
- $b = 5$ → graf protíná osu $y$ v bodě $(0,5)$.

## 3. Kvadratická funkce

- Předpis:  
  $y = ax^2 + bx + c$
- Graf je **parabola**.
  - Pokud $a > 0$ → parabola otevřená nahoru.
  - Pokud $a < 0$ → parabola otevřená dolů.

**Příklad:**  
$y = x^2 - 4$  
Parabola, která jde nahoru a protíná osu $y$ v bodě $(0, -4)$.

## Jak poznám, jestli je funkce rostoucí nebo klesající?

Podívám se na **koeficient u $x$**:

- Když $a > 0$, graf **roste** (stoupá zleva doprava).
- Když $a < 0$, graf **klesá**.
- Když $a = 0$, je to **konstantní funkce** (vodorovná čára).

