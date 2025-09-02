# Kvantifikátory

## 1. Univerzální kvantifikátor

Značka: $\forall$  
Čtení: „všechna“, „pro všechna“

$$
\forall x \in A : P(x)
$$

Výrok: Pro každé $x$ v množině $A$ platí vlastnost $P(x)$.

Všichni v A musí poslouchat pravidlo P(x). Pokud jeden jediný to nesplní, celé tvrzení je **nepravdivé**

### Příklad

**Pravda:**  
$\forall x \in \mathbb{N},\  x + 0 = x$  
(Pro každé přirozené číslo platí, že když k němu přičtu nulu, nic se nezmění.)

**Lež:**  
$\forall x \in \mathbb{N},\  x > 3$  
(Není pravda, protože $1,2$ nejsou větší než 3.)

## 2. Existenční kvantifikátor

Značka: $\exists$  
Čtení: „existuje“

$\exists x \in A : P(x)$

Výrok: Existuje alespoň jedno $x$ v množině $A$, které splňuje vlastnost $P(x)$.  

Stačí, aby **jedno** $x$ vyhovovalo, a výrok je pravdivý.


### Příklad

**Pravda:**  
$\exists x \in \mathbb{N},\ x^2 = 25$  
(Existuje přirozené číslo $x$, jehož druhá mocnina je 25. → $x=5$)

**Lež:**  
$\exists x \in \mathbb{N},\ x^2 = -4$  
(Není žádné přirozené číslo, jehož druhá mocnina je záporná.)


### Poznámka
$\exists !$ = „existuje právě jedno“


## 3. Negace kvantifikátorů

### a) Negace univerzálního kvantifikátoru

$$
\lnot \big(\forall x \in A : P(x)\big) \equiv \exists x \in A : \lnot P(x)
$$

**Slovy:**  
,,Není pravda, že všichni poslouchají pravidlo" znamená ,,Existuje někdo, kdo ho neplní."

**Příklad:**  
$\lnot (\forall x \in \mathbb{N} : x > 0) \equiv \exists x \in \mathbb{N} : x < 0$  

(Není pravda, že všechna přirozená čísla jsou větší než nula → Existuje přirozené číslo, které není větší než nula.)

### b) Negace existenčního kvantifikátoru

$$
\lnot \big(\exists x \in A : P(x)\big) \equiv \forall x \in A : \lnot P(x)
$$

**Slovy:**  
,,Není pravda,že někdo pravidlo splnil" znamená ,,Všichni ho nesplnili"

**Příklad:**  
$\lnot (\exists x \in \mathbb{N} : x < 0) \equiv \forall x \in \mathbb{N} : x \geq 0$  

(Neexistuje žádné přirozené číslo menší než 0, znamená ,,Každé přirozené číslo je větší nebo rovno 0" )

