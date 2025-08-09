
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

<img width="626" height="617" alt="image" src="https://github.com/user-attachments/assets/458e57e7-cdce-43bc-86ce-58aca29ec5db" />


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

### Jak funguje alokace stacku?

- **Stack** je oblast paměti používaná pro ukládání lokálních proměnných, argumentů funkcí a návratových adres.
- Paměť se zde alokuje ve **souvislých blocích** (rámcích – *stack frames*) v rámci *call stacku*.
- **Velikost paměti pro každou lokální proměnnou** je známá už při kompilaci, takže alokace probíhá velmi rychle.
- Když je funkce zavolána, vytvoří se nový *stack frame* pro její proměnné a argumenty.
- Programátor **neřeší** explicitní alokaci ani dealokaci.
- Tento způsob alokace se často označuje jako **dočasné přidělení paměti** (*temporary memory allocation*).
- Po ukončení funkce **se rámec uvolní automaticky** pouhým posunutím *ukazatele* na vrchol stacku.
- Jakmile funkce dokončí provádění, alokovaná paměť je **automaticky uvolněna**.



#### Klíčové vlastnosti přidělování stacku

- Paměť je dostupná **pouze** během běhu funkce (resp. do ukončení jejího *stack frame*).
- Automatické uvolnění probíhá po **skončení funkce**.
- Přeplnění stacku (*stack overflow*) může nastat např. při příliš hluboké rekurzi nebo při alokaci příliš velkých lokálních proměnných:
    - Java: ```java.lang.StackOverflowError```
    - C/C++: obvykle *segmentation fault* nebo chyba typu *stack overflow*.
- Paměť na stacku je **izolovaná pro každé vlákno** (každé má svůj vlastní stack).
- Alokace i dealokace jsou **rychlejší** než u heapu, protože probíhají pouhou změnou ukazatele (*stack pointeru*).


####  Co znamená „každé vlákno má svůj vlastní stack“?

**Co je vlákno**

- **Vlákno** (*thread*) je samostatná „lajna“ provádění instrukcí v rámci programu.
- Jeden proces může mít **více vláken**, která běží souběžně a sdílí stejný **heap** (tedy data), ale každý má vlastní **stack**.

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/ebea1192-7677-4014-b94d-05fe7eee1ce0" />


**Proč má vlákno vlastní stack**

- Stack obsahuje **lokální proměnné, návratové adresy a argumenty funkcí**.
- Kdyby se stack sdílel mezi vlákny, docházelo by k **chaosu**:
    - vlákna by si přepisovala lokální proměnné
    - návratové adresy by se pletly
    - program by padal
- Proto OS při vytvoření nového vlákna **alokuje nový stack jen pro něj**.

**Praktický příklad**

Představ si, že máš dva kuchaře (vlákna), kteří pracují ve stejné kuchyni (proces).

- **Heap** = společná spižírna, kde jsou všechny ingredience (sdílená data).
- **Stack** = osobní pracovní stůl každého kuchaře, kde má svoje nástroje a aktuální recept (lokální proměnné a stav funkcí).

Každý kuchař si na svém stole dělá pořádek po svém a nepotřebuje, aby mu tam druhý sahal.



### Jak funguje alokace heapu?

- **Heap** je oblast paměti určená pro **dynamickou alokaci** – tedy pro objekty a data, jejichž velikost a životnost nejsou známy při kompilaci.
- Na rozdíl od **stacku** není paměť automaticky uvolněna po skončení funkce; zůstává alokována, dokud ji:
    - **programátor neuvolní ručně** (C/C++)
    - **neodstraní garbage collector (GC)** (Java, Python)

**Rozdíly podle programovacího jazyka**

**C/C++**

- **Správa paměti**: plně manuální – alokace (```new```, ```malloc```) a dealokace (```delete```, ```free```) musí být výslovně řízeny programátorem.
- **Chyby**: zapomenuté uvolnění → *memory leak*, předčasné uvolnění → *dangling pointer*.
- **Umístění objektů**: objekty mohou být **na stacku** (např. ```MyClass obj;```) nebo **v heapu** (```MyClass* p = new MyClass();```).

**Java**    

- **Správa paměti**: automatická pomocí garbage collectoru.
- **Umístění objektů**: všechny objekty (instanční data) jsou v heapu, ale odkazy na ně se obvykle ukládají na stack (v rámci *stack frame vlákna*).
- **Kategorie heapu (JVM)**:
    - **1. Young Generation** – nové objekty, častý *minor GC*.
    - **2. Old Generation** – dlouho žijící objekty, méně častý *major GC*.
    - **3. PermGen ≤7 / Metaspace (Java ≥8)** – metadata tříd a metody;  PermGen měla pevnou velikost, Metaspace je v nativní paměti.

**Python** 

- **Správa paměti**: automatická – kombinace **počítání referencí** a **garbage collectoru** pro cyklické reference.
- **Umístění objektů**: všechny objekty (včetně čísel, seznamů atd.) jsou v heapu; proměnné jsou jen odkazy na tyto objekty.

#### Vlastnosti heap paměti

- **Životnost objektů**: dokud je neodstraní programátor (C/C++) nebo GC (Java/Python).
- **Sdílenost**: heap je přístupný všem vláknům v procesu → vyžaduje synchronizaci při paralelním přístupu.
- **Výkon**: pomalejší než stack kvůli složitější správě (alokace, dealokace, GC).
- **Velikost**: obvykle větší než stack, ale omezená dostupnou pamětí a konfigurací (např. ```-Xmx``` v JVM).

- **Chyby při zaplnění**:
    - Java: ```java.lang.OutOfMemoryError```
    - C++: výjimka ```std::bad_alloc``` nebo ukončení programu


## 📌 2. Bitové Operace

- Bitové operace jsou operace, které pracují **přímo na úrovni jednotlivých bitů** proměnné (0 a 1).
-  Používají se pro:
    - **nízkoúrovňovou manipulaci** s daty
    - **optimalizaci výkonu a paměti**
    - práci s **flagy, maskami a binárními protokoly**
        - **Flagy** = příznaky – jednotlivé bity, které označují nějaký stav (např. „uživatel je přihlášen“, „má oprávnění admina“).
        -  **Maska** = binární číslo, které použiješ k „vytažení“ nebo „nastavení“ jen určitých bitů.
        -  **Binární protokoly** = formáty dat, kde se konkrétní bity používají pro konkrétní význam (např. v síťové komunikaci).
    - nastavování, mazání nebo přepínání jednotlivých bitů v hodnotě

**V praxi**

- **Oprávnění uživatele** – jeden int může obsahovat info, jestli může číst, psát, mazat.
- **Síťové hlavičky** – TCP/UDP protokoly používají jednotlivé bity k označení příznaků jako SYN, ACK, FIN.
- **Grafika** – barva pixelu v RGB může být uložena v jednotlivých bitech.

**Příklad** – test oprávnění:

```C
#define PERM_READ   (1 << 0)
#define PERM_WRITE  (1 << 1)
#define PERM_DELETE (1 << 2)

int permissions = PERM_READ | PERM_WRITE;
if (permissions & PERM_WRITE) {
    // má právo zapisovat
}
```


**Nastavování, mazání nebo přepínání jednotlivých bitů**

**Co to znamená**

- Máš proměnnou a potřebuješ **zapnout (1)**, **vypnout (0)** nebo **invertovat (přepnout)** konkrétní bit, aniž bys měnil ostatní.

**V praxi**

- Ovládání LED diod, motorů, senzorů (každý bit řídí jiný kanál).
- Nastavení konfigurace zařízení přes bity v jeho registrech.
- Komprese – balení více hodnot do jedné proměnné.

```C
int value = 0b00001000;

// zapnout 1. bit
value |= (1 << 1); // 00001010

// vypnout 3. bit
value &= ~(1 << 3); // 00000010

// přepnout 1. bit
value ^= (1 << 1); // 00000000
```


### Základní Bitové Operace

| Operace | Symbol | Popis | Příklad (8 bitů) |
|---------|--------|-------|------------------|
| **AND** | `&` | Bitový součin – výsledek 1 jen když oba bity jsou 1 | `1100 & 1010 = 1000` |
| **OR** | `\|` | Bitový součet – výsledek 1, když aspoň jeden bit je 1 | `1100 \| 1010 = 1110` |
| **XOR** | `^` | Exkluzivní OR – výsledek 1, když je přesně jeden bit 1 | `1100 ^ 1010 = 0110` |
| **NOT** | `~` | Bitová negace – převrátí všechny bity | `~1100 = 0011` (v doplňkovém kódu závisí na velikosti typu) |
| **SHIFT LEFT** | `<<` | Posun vlevo – násobí hodnotu mocninou dvou | `0001 << 2 = 0100` |
| **SHIFT RIGHT** | `>>` | Posun vpravo – dělí hodnotu mocninou dvou | `1000 >> 2 = 0010` |

#### Jak ovlivňují proměnné

- **Změna konkrétního bitu**
    -  Pomocí AND/OR/XOR můžeš zapínat, vypínat nebo přepínat jednotlivé bity bez dotyku ostatních.

```C
flags = flags | 0b00000100;  // zapnutí 3. bitu
flags = flags & ~0b00000100; // vypnutí 3. bitu
```

- **Kompaktní uložení dat**
    -  Místo více proměnných můžeš mít jednu proměnnou, kde každý bit reprezentuje stav (tzv. bitmask).

```TEXT
bit 0 = má přístup k čtení
bit 1 = má přístup k zápisu
bit 2 = je administrátor
```

- **Rychlé násobení/dělení**
    -  Posun vlevo (```<<```) = násobení 2ⁿ, posun vpravo (```>>```) = dělení 2ⁿ.
    -  Výhodné při optimalizaci nízkoúrovňového kódu.
- **Nízká úroveň komunikace**
    -  Bitové operace se používají při práci s hardwarem, síťovými protokoly nebo kompresí dat, kde je nutné číst/zapisovat jednotlivé bity.

#### Vliv na typy proměnných

**1. Celá čísla (int, unsigned int, short, long)**

- Bitové operace jsou pro **celá čísla** přirozené, protože jejich binární reprezentace přímo odpovídá tomu, s čím pracuješ (každý bit má jasnou váhu: 1, 2, 4, 8, …).

- **Unsigned** (bezznaménková) čísla se chovají nejpředvídatelněji, protože všechny bity jen vyjadřují kladné hodnoty.

- **Signed** (se znaménkem) čísla mají jeden bit (nejvyšší) vyhrazený pro znaménko a používají **doplňkový kód** (*two's complement*) → to ovlivňuje výsledky posunů.

**Příklad**

```C
unsigned int a = 5;     // 00000101
unsigned int b = a << 2; // 00010100 = 20 (Používáme 10 soustavu!)
```
U unsigned není problém, protože není bit znaménka.

**2. Záporná čísla**

- Většina moderních architektur používá **doplňkový kód** pro reprezentaci záporných čísel.
- To znamená, že např. ```-1``` je uloženo jako všechny bity = 1 (```11111111``` v 8bit).
- **Posun vlevo** (<<) funguje u záporných čísel stejně jako u kladných (bity se prostě posunou), ale může dojít k přetečení.
- **Posun vpravo** (>>) má dva typy:
    - **Aritmetický posun** – zachová znaménko (doplňuje vlevo 1 u záporných čísel).
    - **Logický posun** – vlevo vždy doplňuje nuly, znaménko se neřeší.
- Některé jazyky pevně definují typ posunu (např. v Javě ```>>``` je aritmetický, ```>>>``` je logický), jiné to nechávají na procesoru.

<img width="768" height="364" alt="image" src="https://github.com/user-attachments/assets/9694b115-8352-48e6-9567-c2bdf838cdb6" />


**Příklad – aritmetický vs. logický posun (8bit):**

```TEXT
-4 = 11111100
Aritmetický >> 1 = 11111110  (zůstává záporné)
Logický     >> 1 = 01111110  (změna znaménka)
```

**3. Desetinná čísla (float, double)**

- Bitové operace se na desetinné typy přímo **neaplikují**, protože jejich bity neznamenají „váhy 1, 2, 4…“ ale jsou uspořádány podle standardu **IEEE 754**:
    - 1 bit znaménko
    - několik bitů exponent
    - několik bitů mantisa (zlomek)
- Pokud potřebuješ měnit bity desetinného čísla, musíš:
    - **1.** Přetypovat na celé číslo stejné velikosti (```reinterpret cast```, ```union```).
    - **2.** Provést bitové operace.
    - **3.** Vrátit zpět na float/double.

**Příklad** – změna znaménka u float:

```C
float f = 3.14;
unsigned int* p = (unsigned int*)&f;
*p ^= 0x80000000; // přepne znaménkový bit
```
---
