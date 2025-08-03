# Základy Programování

## Proměnné

Proměnná je pojmenované místo v paměti (RAM), které uchovává určitou hodnotu. Klíčové vlastnosti proměnných:

- **Proměnlivost** – hodnota se může v průběhu času měnit, odtud vzniká název *proměnná*.
- **Jméno, typ a hodnota** – každá proměnná má své **jméno**, **typ** a **hodnotu**.
- **Deklarace** – proměnná musí být deklarována dříve, než je použita
  *(výjimku tvoří jazyky jako Python, kde se deklarace provádí implicitně)*.
- **Datový typ** – určuje, jaký druh dat může proměnná obsahovat a kolik paměti zabere.

---

## Datové Typy

Datový typ definuje:

- Určuje jaké data může proměnná držet a kolik paměti využije.
- Jaké operace je možné s danými daty provádět.

### Primitivní datové typy

Základní, vestavěné typy dostupné ve většině programovacích jazyků:

| Typ         | Popis                                | Příklad         | Velikost (bajty) |
|-------------|----------------------------------------|------------------|-------------------|
| `int`       | Celé číslo                            | `42`             | 4                 |
| `float`     | Desetinné číslo (nižší přesnost)      | `3.14`           | 4                 |
| `double`    | Desetinné číslo (vyšší přesnost)      | `3.1415926`      | 8                 |
| `char`      | Jeden znak (ASCII)                    | `'A'`            | 1                 |
| `bool`      | Logická hodnota                       | `true`, `false`  | 1 nebo více*      |


---

### Neprimitivní (referenční / složené) datové typy

Složitější datové struktury složené z primitivních typů. Jejich velikost je proměnlivá a závisí na obsahu:

| Typ               | Popis                                                                 | Příklad                          |
|-------------------|------------------------------------------------------------------------|-----------------------------------|
| `string`          | Sekvence znaků (`char[]`), často reprezentuje text                     | `"Ahoj"`                          |
| `array`           | Pole s pevnou délkou, typicky s prvky stejného typu. V některých jazycích (např. Python, JavaScript) může obsahovat různé datové typy. | `[1, 2, 3]` nebo `[1, "dva", True]` |
| `list`            | Dynamická kolekce, umožňuje přidávat/ubírat prvky, často řazená        | `[1, 2, 3]`                       |
| `tuple`           | Neměnitelná (immutable) sekvence – po vytvoření nelze měnit obsah      | `(1, "Ahoj", True)`              |
| `set`             | Neřazená množina unikátních hodnot (žádné duplikáty)                   | `{1, 2, 3}`                       |
| `dictionary`      | Kolekce dvojic klíč–hodnota, klíče jsou unikátní                       | `{"jméno": "Anna", "věk": 25}`   |
| `class` / `object`| Uživatelsky definovaný typ s vlastnostmi a metodami                    | `Person(name, age)`              |

```python
# Python
a = 5             # int
b = 3.14          # float
c = "hello"       # string
d = True          # boolean
```

```cpp 
// C++
int a = 5;
float b = 3.14f;
std::string c = "hello";
bool d = true;
```

*Tip*: V některých jazycích (např. C, Java) je potřeba typ proměnné definovat při deklaraci. V jiných (např. Python, JavaScript) je určován automaticky podle přiřazené hodnoty.

## Operátory

Operátory jsou symboly, které provádějí operace s proměnnými a hodnotami.

### Typy operátorů

| Typ operátoru        | Popis                                         | Příklady                                                  |
|----------------------|-----------------------------------------------|------------------------------------------------------------|
| **Aritmetické**      | Základní matematické výpočty                  | `+`, `-`, `*`, `/`, `%`                                    |
| **Relační**          | Porovnání dvou hodnot (vrací `true`/`false`) | `==`, `!=`, `<`, `>`, `<=`, `>=`                           |
| **Logické**          | Práce s pravdivostními hodnotami              | `and`, `or`, `not` *(Python)*<br>`&&`, `\|\|`, `!` *(C++/Java)* |
| **Přiřazovací**      | Přiřazení a změna hodnoty proměnné            | `=`, `+=`, `-=`, `*=`, `/=`, `%=`                          |
| **Unární / Binární** | Podle počtu operandů (1 / 2)                  | `-a` (unární), `a + b` (binární)                           |

- *Poznámka*: Operátory mohou mít různé priority a asociativitu, což ovlivňuje pořadí vyhodnocení ve výrazu. Například násobení (*) má vyšší prioritu než sčítání (+).

---

```cpp
// C++
int a = 5 + 3;              // Aritmetický operátor (+), přiřazení (=)
if (a > 5 && a < 10) {      // Relační operátory (> , <), logický operátor (&&)
    std::cout << "Valid";   // Výstup na obrazovku
}
```

## Řízení Toku

Způsob, jakým program činí rozhodnutí nebo opakuje akce na základě podmínek.

Řízení toku určuje, jak program rozhoduje, které části kódu se vykonají a kolikrát.  

---

### Hlavní řídicí konstrukce

- **`if`, `else if`, `else` – Podmíněné vykonání**
  - **Kdy použít:** Pokud potřebuješ provést různé akce podle hodnoty proměnné nebo výsledku výrazu.
  - **Příklad:**
    ```cpp
    if (teplota > 100) {
        vypnoutOhrev(); // chrání hardware před přehřátím
    } else if (teplota > 50) {
        zpomalitOhrev();
    } else {
        zapnoutOhrev();
    }
    ```
---

- **`switch` – Více větví rozhodování**
  - **Kdy použít:** Pokud máš více pevných hodnot, podle kterých chceš provést různé akce (např. reakce na klávesy, režimy zařízení).
  - **Příklad:**
    ```cpp
      char key = 'A';
      switch (key) {
        case 'W': moveUp(); break;
        case 'S': moveDown(); break;
        case 'A': moveLeft(); break;
        case 'D': moveRight(); break;
        default:  idle(); break; // default, pakliže, by zmáčkl jakoukoli jinou klávesu.
      }
    ```
---

- **`for` – Cyklus s počítadlem**
  - **Kdy použít:** Pokud potřebuješ vykonat blok kódu pevně daný počet opakování (např. čtení 100 hodnot ze senzoru).
  - **Příklad:**
    ```cpp
    for (int i = 0; i < 100; i++) {
        nactiHodnotuZeSenzoru();
    }
    ```
  - **Souvislost s hardwarem:** Procesor provádí opakované *inkrementace* a *porovnání*, poté *skok zpět* na začátek cyklu.

---

- **`while` – Cyklus s podmínkou před vstupem**
  - **Kdy použít:** Pokud nevíš, kolikrát se cyklus provede, ale má běžet dokud platí určitá podmínka.
  - **Příklad:**
    ```cpp
    while (teplota < 80) {
        zapnoutOhrev();
    }
    ```
---

- **`do while` – Cyklus s podmínkou po provedení**
  - **Kdy použít:** Pokud potřebuješ, aby se kód provedl alespoň jednou, bez ohledu na počáteční stav podmínky.
  - **Příklad:**
    ```cpp
    do {
        prectiDataZeSeriovehoPortu();
    } while (!dataPlatna());
    ```
  ---

> **Shrnutí:**  
> Řídicí příkazy existují, protože procesor potřebuje možnost **měnit tok instrukcí** podle aktuální situace (stav proměnných, vstup od uživatele, data ze senzorů).  

## Funkce 

### Proč Používat Funkce?

- **Zamezení opakování kódu** – vyhýbání se duplikování stejné logiky
- **Modularita** – kód je rozdělený na logické části (snáze se čte i ladí)
- **Srozumitelnost** – jasně pojmenovaná funkce napoví, co dělá, bez nutnosti číst detaily


### Vstupy a výstupy

- **Parametry (argumenty)** – hodnoty předané funkci při volání
- **Návratová hodnota** – výstup, který funkce vrací volajícímu kódu



```cpp
// C++

// Deklarace a definice funkce
int add(int a, int b) {
    return a + b;  // Vrací součet obou parametrů
}

// Volání funkce
std::cout << add(2, 3);  // Výstup: 5
```

> **Poznámka:**  
> V některých programovacích jazycích je nutné při deklaraci funkce nebo proměnné **uvést datový typ** (např. `int`, `float`, `string`), protože tyto jazyky používají **statické typování**.  
> Příklady: `C`, `C++`, `Java`, `C#`
>
> Naopak existují jazyky s **dynamickým typováním**, kde se typ proměnné určuje automaticky podle přiřazené hodnoty.  
> Příklady: `Python`, `JavaScript`, `Ruby`
>
> V dynamicky typovaných jazycích neuvádíš typ proměnné – například:
> ```python
> # Python
> x = 5          # Python automaticky rozpozná, že x je typu int
> def add(a, b): # žádné typy u parametrů
>     return a + b
> ```


## Datové Struktury

Datové struktury jsou **základem algoritmického myšlení**. Správná volba ovlivňuje **výkon** programu i **čitelnost** kódu.

Používáme je k organizaci dat tak, aby byly přístupné, manipulovatelné a efektivně spravované.

---

### Array

> *Představ si školní chodbu se skříňkami – každá má své číslo (index) a pevné místo.*

- Prvky jsou v paměti uloženy **souvisle za sebou**
- Přístup podle indexu je **extrémně rychlý: O(1)**
- **Nevýhoda:** Pokud je pole plné, je potřeba vytvořit nové a staré přepsat → **kopírování: O(n)**

```text
Původní pole: [1, 2, 3]
Nové pole po přidání 4: [1, 2, 3, 4]
```

- Vymazání prvku = posunutí všech následujících → **O(n)**  
  *(mazání na konci je ale O(1))*

---

### Linked List

> *Představ si vlak, kde musíš projít každý vagon, než najdeš ten správný.*

- Každý prvek (**uzel**) obsahuje hodnotu + ukazatel (*Pointer*) na další
- Přístup k náhodnému prvku: **O(n)** (musíš projít všechny, aby jsi na něj narazil)
- Vložení/mazání uprostřed seznamu: **O(1)** – stačí upravit ukazatele

---

### Stack (Zásobník)

> *Jako věž z chipsů – poslední chips položený navrch bude první, který sníš.*

- **LIFO – Last In, First Out**
- Pokud bych chtěl ve výše zmíněné analogii se dostat na spodek balíčku, musel bych postupně zvrchu dolů všechny sníst.
- `push()` a `pop()` Přídávání a Odebírání **O(1)**
- Hledání prvku = **O(n)**

---

### Queue (Fronta)

> *Řada u pokladny – kdo přijde první, ten jde první.*

- **FIFO – First In, First Out**
- Když přijdou nové data musí se zařadit do zadu, stejně jako v řadě u pokladny.
- Přidávání (`enqueue`) na konec, odebírání (`dequeue`) z počátku → **O(1)**
- Nelze libovolně přistupovat k prvkům (jako v arrayi)

---

### Heap (Prioritní fronta)

> *Představ si pyramidu z krabic, kde nahoře je vždy nejmenší nebo největší krabice.*

- **Min Heap**: rodič < děti  
  **Max Heap**: rodič > děti
- Přístup k nejvyšší prioritě (root): **O(1)**
- Přístup k k libovolným prvkům v heapu: **0(n)**
- Vložení/mazání: **O(log n)** – kvůli nutnému „přebudování“ pyramidy (díky vlastnosti heapu, kdy vztah rodič-dítě je vetší nebo menší se posune na správnou pozici. Heapy jsou ve skutečnosti vyvážené binární stromy.)
- extrémně efektivní jsou operace mazání a vkládání ve srovnání s lineárními datovými strukturami, jako jsou arraye nebo linked lists.

---

### Hashmap

> *Představ si kancelář, kde má každý zaměstnanec svoji poštovní schránku s číslem.  
> Když přijde dopis pro Johna, místo procházení všech schránek víš rovnou, že John má schránku č. 4.  
> Sally má schránku č. 5. Každý přesně ví, kam co patří.*

HashMap je datová struktura, která ukládá hodnoty podle unikátních klíčů. K určení pozice pro uložení klíče se používá hashovací funkce, která převádí klíč na index v interním arrayi.

- Ukládá **klíč–hodnota** páry (`key -> value`)
- Díky hashovací funkci je možné najít hodnotu extrémně rychle → **O(1)**
- Umožňuje rychlý přístup, přidání i smazání položky

#### Hashovací kolize – co když dvě osoby chtějí stejnou schránku?

> *Představ si, že přijde nový zaměstnanec Andy. Jméno „Andy“ má stejně jako „John“ čtyři písmena.  
> Pokud by hashovací funkce určovala číslo schránky podle délky jména, oba by skončili na pozici č. 4.*

To je tzv. **kolize** – situace, kdy dva různé klíče směřují na stejnou pozici.  
Aby nevznikl chaos ve schránce, musíme to nějak vyřešit:

##### Možnosti řešení kolizí:
- **Řetězení (chaining):** ve schránce bude malý „seznam dopisů“ – více položek na jednom místě
- **Lineární prohledávání:** pokud je schránka obsazená, hledáme další volnou (č. 5, č. 6, …)

- **Přístup k prvku podle klíče**: běžně **O(1)** – přesně víme, kam jít
- **V nejhorším případě**: až **O(n)** – pokud dojde k mnoha kolizím a všechny položky skončí v jednom řetězci (např. **linked list**), musíme projít celý seznam hodnot ručně

---