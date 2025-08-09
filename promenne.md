
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


## Volání funkcí → nový stack frame → nové instance proměnných

Kdykoli zavoláš funkci, počítač potřebuje někam uložit její proměnné, parametry a návratovou adresu – tedy místo, kam se má vrátit, až funkce skončí.

Proto se pro každé volání funkce vytvoří nový "rámec" (stack frame) na tzv. zásobníku (stack).


```C 
def pozdrav(jmeno):
    zprava = "Ahoj, " + jmeno
    print(zprava)

pozdrav("Tereza")
```

Když zavoláš ```pozdrav("Tereza")```, vytvoří se nový stack frame, který obsahuje:

- parametr ```jmeno = "Tereza"```
- lokální proměnnou ```zprava```


Po skončení funkce se tento stack frame **automaticky smaže** → tyto proměnné už **neexistují**.

### Rekurze → každé volání má vlastní kopii proměnných

Rekurze je, když funkce volá sama sebe.

A protože každé volání vytváří **nový stack frame**, každá úroveň rekurze má:

- své vlastní proměnné
- svůj vlastní kontext

Jak to vypadá?

```Python
def faktorial(n):
    if n == 1:
        return 1
    else:
        return n * faktorial(n - 1) # rekurze
```

Když zavoláš ```faktorial(3)```, děje se tohle:

```scss
faktorial(3)
 → faktorial(2)
   → faktorial(1)
```

Každý z těchto tří výpočtů má **vlastní** ```n```:


- První ```n = 3```
- Druhé ```n = 2```
- Třetí ```n = 1```

A každá funkce čeká, až se vyřeší ta „vnořená pod ní“ – až pak může vrátit výsledek.

### Heap → objekty žijí dál, dokud je neodstraníš

- Heap je **část paměti**, kterou program používá na ukládání **objektů** nebo **dat**, **jejichž velikost a životnost neznáš předem.**

- Do heapu se ukládají věci, které **vytvoříš dynamicky** – například přes ``new`` v C++ nebo při vytvoření objektu v Javě.

Proč tam objekty žijí dál?

- Když vytvoříš proměnnou na **stacku** (např. int x = 5;), ta proměnná zanikne sama, jakmile skončí blok kódu (funkce).

- Když něco uložíš do heapu, **operační systém nebo běhové prostředí neví, kdy to má smazat** – proto to tam zůstane, dokud to **neodstraníš** (v C/C++ přes ``delete`` nebo ``free``), nebo dokud si to nevezme **garbage collector** (v Javě, Pythonu).

```C++
void funkce() {
    int x = 5; // stack → zanikne po skončení funkce
    int* p = new int(10); // heap → přežije konec funkce

    // ... něco s p
} // tady se x smaže, ale p pořád ukazuje na 10 v heapu

```

- Pokud po skončení funkce nezavoláš ```delete p;```, ta 10 v paměti tam **zůstane**, i když už na ni nemáš odkaz → **memory leak**.

- **Memory leak** = paměť, kterou program zabral, ale už ji neumí uvolnit, **protože ztratil všechny odkazy na ni**.
Výsledek? Paměť se „vyplýtvá“ a program může časem **spadnout** nebo **zpomalit**.

**Java/Python**

- V Javě a Pythonu máš heap také, ale je tam **garbage collector**, který čas od času smaže objekty, na které už nevede žádná proměnná.

-  Ale dokud **máš někde odkaz na objekt**, bude žít dál.

```Java
List<String> seznam = new ArrayList<>();
seznam.add("Ahoj"); // objekt "Ahoj" je v heapu

// pokud proměnnou seznam nastavíš na null a nikde jinde není odkaz,
// GC ho smaže při příštím úklidu
```


---