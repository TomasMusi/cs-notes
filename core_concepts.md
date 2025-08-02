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

| Typ         | Popis                                                 | Příklad                  | Velikost (bajty)       |
|-------------|--------------------------------------------------------|---------------------------|--------------------------|
| `string`    | Sekvence znaků (`char[]`)                             | `"Ahoj"`                  | Závisí na délce + metadata *(např. 5+)* |
| `array`     | Pevně velké pole prvků stejného typu                  | `[1, 2, 3]`               | `počet prvků × velikost typu` |
| `list`      | Dynamická kolekce (např. spojový seznam, vektor)      | `[1, 2, 3]`               | Různé (např. 24 bajtů + data) |
| `class` / `object` | Uživatelsky definovaný typ – obsahuje vlastnosti a metody | `Person(name, age)`       | Závisí na polích + referencích |



*Tip*: V některých jazycích (např. C, Java) je potřeba typ proměnné definovat při deklaraci. V jiných (např. Python, JavaScript) je určován automaticky podle přiřazené hodnoty.




