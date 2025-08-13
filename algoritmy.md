# Algoritmy a časová složitost

**Big-O Notation** – proč to existuje


Představ si, že máš program a zajímá tě, jak dlouho mu bude trvat práce, když **roste množství vstupních dat**.



| Big-O          | Popis                                          | Příklad                                   |
| -------------- | ---------------------------------------------- | ----------------------------------------- |
| **O(1)**       | Konstantní čas – nezáleží na velikosti vstupu  | Přístup k prvku v poli podle indexu       |
| **O(log n)**   | Logaritmický čas – roste pomaleji než lineárně | Binární hledání                           |
| **O(n)**       | Lineární čas – zdvojnásobení dat = 2× práce    | Průchod pole                              |
| **O(n log n)** | Rychlé třídicí algoritmy                       | Merge sort, Quick sort                    |
| **O(n²)**      | Kvadratický čas – dvojité smyčky               | Bubble sort, porovnávání každého s každým |
| **O(2ⁿ)**      | Exponenciální – katastrofa pro větší n         | Generování všech podmnožin                |
| **O(n!)**      | Faktorová složitost – ještě horší              | Permutace všech prvků                     |


## Základní algoritmy

### 2.1 Třídění

Třídění = seřazení dat podle určitého klíče.

**Bubble sort** – *O(n²)*

- Porovnává sousedy a prohazuje je. Jednoduchý, ale pomalý.

```PYTHON
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        # Poslední i prvků už je na správném místě
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                # Prohoď
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

# Příklad použití
data = [5, 1, 4, 2, 8]
bubble_sort(data)   
print(data)  # [1, 2, 4, 5, 8]

```

**Merge sort** – *O(n log n)*

- Rozdělí seznam na poloviny, rekurzivně je seřadí a pak spojí.

```PYTHON
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0

    # Procházení obou seznamů a přidávání menšího prvku
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    # Přidej zbytek
    result.extend(left[i:])
    result.extend(right[j:])
    return result

# Příklad použití
data = [5, 1, 4, 2, 8]
sorted_data = merge_sort(data)
print(sorted_data)  # [1, 2, 4, 5, 8]
```

**Quick sort** – *O(n log n)* průměr, *O(n²)* nejhorší případ

- Vybere pivot, rozdělí na menší a větší, rekurzivně seřadí.

```PYTHON
def quick_sort(arr):
    if len(arr) <= 1:
        return arr

    pivot = arr[len(arr) // 2]  # střední prvek jako pivot
    smaller = [x for x in arr if x < pivot]
    equal = [x for x in arr if x == pivot]
    greater = [x for x in arr if x > pivot]

    return quick_sort(smaller) + equal + quick_sort(greater)

# Příklad použití
data = [5, 1, 4, 2, 8]
sorted_data = quick_sort(data)
print(sorted_data)  # [1, 2, 4, 5, 8]
```

### 2.2 Vyhledávání

**Lineární hledání** – *O(n)*

- Projdu seznam od začátku, dokud nenajdu prvek.

**Binární hledání** – *O(log n)*

- Funguje jen na seřazeném seznamu:
    -  Podívám se doprostřed, rozhodnu se, zda hledat vlevo nebo vpravo, opakuju.

**TIP** 

- Když máš hodně hledání, ale málo změn dat → seřaď jednou, pak používej binární hledání.
- Nebo použij **HashMap** *(O(1)* průměrně).

### 2.3 Grafové algoritmy

Graf = uzly (nodes) + hrany (edges).

- **BFS (Breadth-First Search)** – prochází graf po vrstvách (O(V+E)).
    - Hodí se pro nalezení nejkratší cesty v neohodnoceném grafu.
- **DFS (Depth-First Search)** – jde do hloubky (O(V+E)).
    - Hodí se pro prohledávání všech možností, detekci cyklů.
- **Dijkstra** – najde nejkratší cestu v ohodnoceném grafu (O(E log V) s prioritní frontou).

### 2.4 Rekurze

Rekurze = funkce volá sama sebe.
```JAVA
int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```
