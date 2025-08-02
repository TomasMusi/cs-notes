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




