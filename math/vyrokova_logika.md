# Výroková logika

Co je to výrok?  
Výrok je věta, která může být pravdivá **(1, ANO)** nebo nepravdivá **(0, NE)**.

## Logické spojky

| Logika          | Co říká                    | Kdy platí                     |
|-----------------|--------------------------|--------------------------------|
| $\lnot A$       | „není A“                   | když A neplatí                |
| $A \land B$     | „A a zároveň B“          | když obě jsou pravdivé         |
| $A \lor B$      | „A nebo B“               | když platí alespoň 1           |
| $A \implies B$  | „jestliže A, pak B“      |  |
| $A \iff B$      | „A právě tehdy, když B“  | když oba jsou stejné (oba pravdivé nebo oba nepravdivé) |


**Konjunkce** - Výsledek je pravda jen tehdy, když oba výroky jsou pravda.

**Disjunkce** - Výsledek je pravda, když alespoń jeden výrok je pravda.

**Implikace** - ,,Jestliže uklidíš pokoj (A), dostaneš zmrlinu (B)"

| A | B | $A \implies B$ | Vysvětlení                           |
|---|---|----------------|---------------------------------------|
| 1 | 1 | 1              | Uklidil si → dostal jsi zmrzlinu                        |
| 1 | 0 | 0              | Uklidil si, ale nedostal jsi ji → neplatí (**nepravda**)       |
| 0 | 1 | 1              | Neuklidil si, ale dostal jsi → platí (OK)                 |
| 0 | 0 | 1              | Neuklidil, nedostal (v pořádku)        |


Implikace je nepravdivá jen tehdy, když první věc platí, ale druhá ne.

**Ekvivalence** - Výsledek je pravda, když oba výroky jsou stejné → oba pravdivé či nepravdivé.