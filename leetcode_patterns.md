# LeetCode Patterns.

Tento soubor je „mapa“ základních technik pro LeetCode. Pojmy jako **array, subarray, substring, linked list, node, edge** nechávám v angličtině.

## Rychlý Checklist

1. **Jsou vstupy malé?** → zkus **Brute Force**.
2. **Mluví se o _substring_ nebo _subarray_?** → **Sliding Window**.
3. **Je to sorted? páry/dvojice/sum?** → **Two Pointers**.
4. **Potřebuješ frequency / O(1) lookup?** → **HashMap (dict)**.
5. **„next greater“, balanced parentheses, undo** → **Stack**.
6. **„K largest / K smallest“** → **Heap (priority queue)**.
7. **prefixy/slovník slov** → **Trie (prefix tree)**.
8. **„nodes/edges/graph/path/connected“** → **Graphs (DFS/BFS)**.

## 1) Sliding Window

### Co to je?

o sliding window uvažujeme jako o způsobu, jak efektivně zpracovat podmnožinu dat tím, že se v daném okamžiku zaměříme pouze na nejrelevantnější část.

### Typy Sliding Window

**Existují dva typy sliding window.**

- 1 Fixed sliding window 
    - fixed sliding window udržuje konstantní délku při posunu přes datovou strukturu
    - úloha zní: najít subarray nebo substring fixní délky (fixed lenght) 

- 2 Dynamic sliding window
    - Dynamic sliding window se na rozdíl od fixed window rozšiřuje a zmenšuje podle podmínek.
    - úloha vyžaduje, abychom našli nejdelší nebo nejkratší subarray/substring, který splňuje danou podmínku


### Kdy použít?

**1) Fixed-size Sliding Window (pevná délka K)**

**Kdy to použít**

Když zadání **výslovně** říká „přesně K“ prvků/znaků:

- „max sum subarray **of size K**“
- „průměr v okně o velikosti K“
- „počet 1’s v každém okně délky K“



### Jak to Vypadá na pozadí?

**1) Fixed-size (K je dané)**

Cíl: „max sum subarray of **size K**“.

**Array:** ```A = [2, 1, 3, 4, 2, 1]```, **K = 3**

Okna (vždy **3** prvky):

- krok 1: ```L=0, R=2``` → okno = ```[2, 1, 3]```
- krok 2: ```L=1, R=3``` → okno = ```[1, 3, 4]```
- krok 3: ```L=2, R=4``` → okno = ```[3, 4, 2]```
- krok 4: ```L=3, R=5``` → okno = ```[4, 2, 1]```

**Update v O(1)**: když posuneš okno, **přičteš** nový prvek na pravé straně a **odečteš** ten, co vypadl vlevo.

**Time**: O(n) (každý prvek přidáš jednou a odečteš jednou)

**2) Dynamic-size (délka se mění podle podmínky)**