
# Proměnné

Proměnná je pojmenované místo v paměti (RAM), které uchovává určitou hodnotu. Klíčové vlastnosti proměnných:

- **Proměnlivost** – hodnota se může v průběhu času měnit, odtud vzniká název *proměnná*.
- **Jméno, typ a hodnota** – každá proměnná má své **jméno**, **typ** a **hodnotu**.
- **Deklarace** – proměnná musí být deklarována dříve, než je použita
  *(výjimku tvoří jazyky jako Python, kde se deklarace provádí implicitně)*.
- **Datový typ** – určuje, jaký druh dat může proměnná obsahovat a kolik paměti zabere.


## 1. Deklarace, inicializace a životní cyklus proměnné

### 🔹 Deklarace

Deklarace je proces, kdy říkáš kompilátoru nebo interpretu, že chceš použít proměnnou – tedy že si rezervuješ pojmenované místo v paměti.

V **staticky typovaných jazycích** (např. C, Java) deklarace zahrnuje i určení datového typu:

```C
int x; // deklarace proměnné typu int
float y; // proměnná typu float
```

V **dynamicky typovaných jazycích** (např. Python, JavaScript) se typ odvodí z hodnoty automaticky:

```Python
x = 10     # Python: deklarace + inicializace
``` 

### 🔹 Inicializace

Inicializace znamená **přiřazení hodnoty** proměnné. Může být provedena ihned při deklaraci, nebo později:

```C
int x = 5;       // deklarace a inicializace současně
int y;           // deklarace
y = 10;          // inicializace dodatečně
```

Inicializace může být i **výsledkem výpočtu** nebo výrazu:

```Python
a = 3 + 4
b = len("text")
```

> V některých jazycích neinicializovaná proměnná obsahuje náhodné (nebo chybové, záleží na kompileru a na samotném systému, takže se pro toto chování používá termín: UB - Undefined Behaviour) hodnoty – např. v C. 


### 🔹 Životní cyklus proměnné

Každá proměnná prochází 3 hlavními fázemi:

**1.** Vytvoření (alokace paměti)

- Paměť je rezervována pro proměnnou. K tomu dochází při deklaraci nebo při vstupu do scope (např. vstup do funkce).

- Scope je měřítko (nebo pravidlo), které určuje, ve které části programu má proměnná platnost – tedy kde je viditelná, použitelná a existuje v paměti.

**2.** Život (aktivní používání)

- Během této fáze můžeš s proměnnou manipulovat, číst její hodnotu, měnit ji nebo ji předat jinam.

```C
int x = 10;
x = x + 5; // aktivní fáze používání
```

**3.** Zánik (dealokace paměti)

- Proměnná přestává existovat – paměť je uvolněna. Záleží na jazyce:

- V C/C++: proměnná na stacku zaniká při opuštění scope, na heapu až po free()/delete
- V Pythonu, JavaScriptu atd.: garbage collector si hlídá, kdy už proměnná není potřeba

## Lokální vs. Globální životní cyklus

- **Lokální proměnná**: žije pouze ve funkci nebo bloku, kde byla deklarována
- **Globální proměnné**: žije po celou dobu běhu programu
- **Statická proměnná**: Static variable je proměnná, která si zachovává svou hodnotu mezi voláními funkcí a je uložena v datovém segmentu namísto ve stacku.

```C
void counter() {
    static int count = 0; // uchovává hodnotu mezi voláními
    count++;
}
```

Co se stane, když zavoláme `counter()` vícekrát?

Při každém volání `counter()`:

Řádek `count++` zvýší hodnotu `count` o 1.

Ale protože `count` je **static**, **pamatuje** si svou hodnotu z posledního spuštění funkce.

Bez `static`, by se `count` při každém volání resetoval na `0`.

```BASH
counter(); // count se stane 1
counter(); // count se stane 2
counter(); // count se stane 3
```


d
---