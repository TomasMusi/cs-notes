# Relace

**Definice:**  
Relace je vztah mezi dvěma prvky z jedné nebo dvou množin.

Formálně:  
$R \subseteq A \times A$  

(tj. množina uspořádaných dvojic)

## Vlastnosti relací

### 1. Reflexivita

$$
\forall a \in A : (a,a) \in R
$$

**Slovy:** Každý prvek je ve vztahu sám se sebou.  

**Příklad:** rovnost $=$ je reflexivní, protože $a = a$.

### 2. Symetrie

$$
\forall a,b \in A : (a,b) \in R \implies (b,a) \in R
$$

**Slovy:** Pokud je $a$ ve vztahu k $b$, pak i $b$ je ve vztahu k $a$.
**Příklad** Přátelství, jestliže já s tebou kámoším, tak i ty semnou.

### 3. Antisymetrie

$$
(a,b) \in R \land (b,a) \in R \implies a = b
$$

**Slovy:** Oba směry platí jen tehdy, pokud jsou to stejné prvky.  
**Příklad** ,,je menší nebo rovno" - nemůže být současně $2 \leq 3$ a $3 \leq 2$

### 4. Tranzitivita

$$
(a,b) \in R \land (b,c) \in R \implies (a,c) \in R
$$

**Slovy:** Pokud $a$ souvisí s $b$ a $b$ souvisí s $c$, pak $a$ souvisí i s $c$.

**Příklad:** relace „být příbuzný“ → pokud $A$ je rodič $B$ a $B$ je rodič $C$,  
pak $A$ je prarodič $C$.
