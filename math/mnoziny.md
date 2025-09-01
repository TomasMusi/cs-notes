# Množiny

Co je to množina? „Skupina čísel nebo prvků.“

Množina A:

$A = \{1,2,3\}$


## Základní znaky a pojmy

| Značka | Význam              | Vysvětlení                                      |
|--------|---------------------|------------------------------------------------|
| $\in$  | „je v“              | $2 \in B \Rightarrow\ 2$ je v množině $B$ |
| $\notin$ | „není v“          | $5 \notin B \Rightarrow\ 5$ není v $B$   |
| $\subseteq$ | „je podmnožina“  | Vše co je v jedné krabičce je i v druhé            |
| $\emptyset$ | „prázdná množina“| krabice, kde nic není                                                |

## Zápis množin

### 1. Vyjmenováním

$A = \{1,2,3\}$

### 2. Popisem vlastností

$B = {\, x \in \mathbb{N} \mid x < 5 \,\}$
(x je z přirozených čísel a zároveň, která jsou menší než 5)



| Značka     | Název             | Význam                                           | Příklad                  |
|------------|------------------|--------------------------------------------------|--------------------------|
| $\mathbb{N}$ | Přirozená čísla  | $1,2,3,4,5,\dots$                               | Vše co je v realitě  |
| $\mathbb{Z}$ | Celá čísla       | $\dots,-3,-2,-1,0,1,2,3,\dots$                  | $-1,3,-5,0,25$           |
| $\mathbb{Q}$ | Racionální čísla | $\mathbb{Q} \in \mathbb{Z}$ (zlomky, desetinná čísla) | $\tfrac{1}{2}, 0.3, -\tfrac{7}{4}$ |
| $\mathbb{R}$ | Reálná čísla     | Všechna čísla na číselné ose                    | odmocniny, $\pi$         |
| $\mathbb{C}$ | Komplexní čísla  | Reálná čísla + imaginární jednotky              | $5i,\, 2-3i$             |


## Racionální číslo
Racionální číslo je každé číslo, které můžeme zapsat jako zlomek dvou celých čísel.  

Například:  
$3 = \tfrac{3}{1}$  

$\mathbb{Q} = \{\, \tfrac{a}{b} \;|\; a \in \mathbb{Z},\; b \in \mathbb{Z},\; b \neq 0 \,\}$

## Celé číslo

Každé celé číslo $\mathbb{Z}$  krom nuly je zároveň racionální číslo.

## Komplexní číslo

důvod proč to vzniklo a co to odlišuje od $\mathbb{R}$ je, že máme imaginární čísla i


$\sqrt{4} = 2$, protože $2 \cdot 2 = 4$  

Ale co $\sqrt{-4}$?  
Neexistuje žádné reálné číslo, které po umocnění na druhou dá $-4$.

Definujeme tedy **imaginární jednotku $i$**:  

$i^{2} = -1$

Například: $\sqrt{-4} = 2i$


komplexní číslo je součet reálné části a imaginární částí.


| Symbol        | Znamená        | Vysvětlení v běžné řeči              | Příklad                                    |
|---------------|----------------|--------------------------------------|--------------------------------------------|
| $\in$         | ,,je prvkem množiny"          | číslo nebo prvek je uvnitř množiny                 | $2 \in \{1,2,3\}$                          |
| $\notin$      | ,,není prvkem množiny"     | „x nepatří do množiny“               | $5 \notin \{1,2,3\}$                       |
| $\subseteq$    | Podmnožina     | „Všechno z levé množiny je i v pravé“                  | $\{1,2\} \subseteq \{1,2,3\}$                |
| $\cup$        | Sjednocení (A nebo B)    | „všechno dohromady“                  | $A \cup B = \{1,2,3,5\}$                   |
| $\cap$        | Průnik (A a zároveň B)         | „Jen to, co je v obou zároveň“                   | $A \cap B = \{2,3\}$                       |
| -   | Rozdíl         | „co zůstane v A, když odeberu prvky B“ | $\{1,2,3\} - \{2,3\} = \{1\}$     |
| $\emptyset$   | Prázdná množina          | množina, která neobsahuje žádný prvek  | $A \cap B = \emptyset$ |
| $\land$       | A zároveň (logická spojka) | Obě podmínky musí být splněné | $A \in \mathbb{N} \land A < 5$ |
| $\lor$        | Nebo (logická spojka)    | platí alespoň jedna podmínka           | $(x=0) \lor (x=1)$                         |
| $\implies$    | Implikuje (jestliže, pak) | jestliže platí první, pak platí druhé | $x>2 \implies x>0$                         |

