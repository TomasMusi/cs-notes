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

