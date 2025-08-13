# Řízení Toku

## Podmínky (if, else if, else, switch)

Podmínky říkají programu:

> "Pokud platí tahle situace, udělej tohle. Pokud ne, zkus jinou situaci. Pokud nic neplatí, udělej tohle."

```if```, ```else if```, ```else```

```JAVA
if (teplota > 30) {
    System.out.println("Je horko!");
} else if (teplota > 20) {
    System.out.println("Je příjemně.");
} else {
    System.out.println("Je chladno.");
}
```
- **if** – test první možnosti.
- **else if** – test další možnosti, pokud předchozí neplatila.
- **else** – výchozí varianta, pokud neplatilo nic.

```switch```

**switch** – alternativa k mnoha ```if```

```JAVA
switch (den) {
    case "Pondělí":
        System.out.println("Začátek týdne");
        break;
    case "Pátek":
        System.out.println("Téměř víkend");
        break;
    default:
        System.out.println("Běžný den");
}
```

### Kdy použít ```switch``` oproti ```If```?

1. Porovnáváš **jednu hodnotu** proti **více konstantám**
```JAVA
switch (command) {
    case "start": start(); break;
    case "stop": stop(); break;
    case "pause": pause(); break;
    default: help();
}
```
→ Čitelnější než deset ```else if```.

2. Máš velký počet možností a každá je konstantní hodnota:
    - U číselných typů (int, enum) může kompilátor vytvořit **jump table** → O(1) čas vyhodnocení.
    - ```if``` musí vyhodnotit všechny podmínky → O(n) v nejhorším případě.

3. Pracuješ s **enumem** (pevně daný seznam možností)

```JAVA
enum Status { NEW, IN_PROGRESS, DONE }

switch (status) {
    case NEW -> System.out.println("Nová úloha");
    case DONE -> System.out.println("Hotovo");
}
```

Kdy použít ```if```?

1. Potřebuješ **složitou podmínku** (více proměnných, >, <, AND, OR).:
```JAVA
if (x > 5 && y < 10 || isSpecialCase(z)) { ... };
```
- to ```switch``` neumí

2. Potřebuješ **porovnávat různá pole nebo více proměnných**:
```JAVA
if (vek > 18 && status.equals("student")) { ... }
```

Extra Tipy:

- **Výkon**
    - U malého počtu možností rozdíl nepoznáš.
    - U velkého počtu a jednoduchých typů (```int```, ```enum```) je ```switch``` rychlejší díky jump table nebo hash lookupu.

- **Čitelnost**
    - ```switch``` je skvělý pro „menu“ scénáře – z kódu je hned jasné, že se vybírá z pevného seznamu možností.
    - ```if``` je lepší pro složité logiky a kombinace podmínek.

### Jak to funguje uvnitř

**If/Else**

- Přeloží se na **branch instrukce procesoru** – procesor provede skok na jinou část kódu podle výsledku podmínky.
- Pokud je hodně větví, CPU musí častěji odhadovat (branch prediction), což může zpomalit.

**switch**

- **Malý počet možností** → kompilátor přeloží switch na sérii if/else.
- **Velký počet číselných hodnot** → použije **jump table**
    -  → to je tabulka adres, kam skočit – přímý skok = **O(1)**.
- **Stringy** → často se přeloží na:
    - Výpočet hash kódu řetězce.
    - Skok podle hash (hash mapa).
    - Ověření shody řetězce pro jistotu (kvůli kolizím).

## Logické operátory

Logické operátory

- ```&&``` (a zároveň)
- ```||``` (nebo)
- ```!``` (negace)

**Short-circuiting**

Pokud je v ```&&``` první část nepravda, druhá se už nekontroluje:
Funguje stejně pro ```||``` – když první je true, druhá se nepočítá.

```JAVA
if (x != 0 && y / x > 2) { ... }
```

**Ternární operátor**
Zkrácená forma if/else:

```JAVA
String status = (vek >= 18) ? "Dospělý" : "Nezletilý";
```

Používej na krátké výrazy, ne na dlouhé bloky → čitelnost je důležitá.

**Čitelnost > zkrácení kódu**
- Napiš kód tak, aby ho někdo další pochopil na první pohled.

```JAVA
// ✅ čitelné
String status = (vek >= 18) ? "Dospělý" : "Nezletilý";

// ❌ nečitelné – složité logiky v ternárním
String status = (vek >= 18 && isCitizen && !isSuspended) ? "Platný" : (vek >= 18 ? "Náhradní" : "Neplatný");
```

**Switch vs. mapa**

- Pokud máš **přiřazení klíč** → **hodnota**, nemusíš psát ```switch```:

```JAVA
// switch verze
switch (den) {
    case 1: return "Pondělí";
    case 2: return "Úterý";
    case 3: return "Středa";
    default: return "Neznámý den";
}

// mapa verze
Map<Integer, String> dny = Map.of(
    1, "Pondělí",
    2, "Úterý",
    3, "Středa"
);
return dny.getOrDefault(den, "Neznámý den");
```

- Mapa (```Map```, ```HashMap```) je **snadněji rozšiřitelná** – nemusíš měnit kód logiky, jen data.

**Řaď podmínky podle pravděpodobnosti**

- CPU má **branch prediction** – snaží se odhadnout, kam skočí dál.
- Když dáš **nejčastější podmínku první**, snižuješ počet špatných odhadů a kód běží rychleji.

```JAVA
// Lepší – častý případ první
if (status == READY) {
    process();
} else if (status == WAITING) {
    waitMore();
} else {
    logError();
}
```

**Vyhýbej se deep-nestingu**
- Více než 2–3 úrovně vnoření (```if``` → ```if``` → ```if```) se špatně čtou.
- Používej **guard clauses** – včasný návrat z funkce.

```JAVA
// ❌ deep nesting
if (user != null) {
    if (user.isActive()) {
        if (!user.isBanned()) {
            sendMessage(user);
        }
    }
}

// ✅ guard clauses
if (user == null) return;
if (!user.isActive()) return;
if (user.isBanned()) return;
sendMessage(user);
```

- Guard clauses **zploští kód**, takže čtenář nemusí sledovat tolik závorek.

## Co je to cyklus?

Cykly jsou způsob, jak **opakovat stejný kus kódu vícekrát**, aniž bys ho musel psát pořád dokola.

Analogie:

- **for** – „Běž 10× kolem hřiště, ať je to přesně 10 kol.“
- **while** – „Běž dokud máš sílu běžet.“
- **do-while** – „Běž aspoň jednou, a pak pokračuj, dokud máš sílu.“
- **foreach** – „Projdi seznam lidí a každému podej ruku.“

### Základní typy cyklů

**for – cyklus s počítadlem**
- Víš přesně, kolikrát chceš opakovat.
- Obsahuje **inicializaci**, **podmínku** a **krok**.

```JAVA
for (int i = 0; i < 5; i++) {
    System.out.println(i); // vypíše 0,1,2,3,4
}
```

**Průběh** 

1. ```int i = 0``` – nastavíme začátek (počítadlo).
2. ```i < 5``` – pokud je pravda, vstoupíme do těla cyklu.
3. ```System.out.println(i)``` – vykoná se.
4. ```i++```  – zvýšíme o 1.
5. Opakujeme, dokud podmínka neplatí.

**while – cyklus dokud platí podmínka**

- Nepředvídáš přesný počet opakování.
- Může proběhnout 0× (když hned od začátku není splněná podmínka).

```JAVA
while (energie > 0) {
    spotrebujEnergii();
}
```

**do-while – cyklus, který proběhne minimálně jednou**

- Podmínka se kontroluje **až po provedení těla**.
```JAVA
do {
    spotrebujEnergii();
} while (energie > 0);
```

**foreach – jednoduché procházení kolekce** 

- Používá se pro **iteraci přes seznamy, pole, kolekce**.
- Nepotřebuješ indexy, jen každý prvek.

```JAVA
for (String jmeno : seznam) {
    System.out.println(jmeno);
}
```

### Chytré používání cyklů

**Minimalizuj práci uvnitř cyklu**

Špatně:

```JAVA
for (int i = 0; i < seznam.size(); i++) { // size() se volá při každé iteraci
    System.out.println(seznam.get(i));
}
```

Lépe:

```JAVA
int size = seznam.size();
for (int i = 0; i < size; i++) {
    System.out.println(seznam.get(i));
}
```

**Používej break a continue**

- ```break``` → ukončí aktuální cyklus hned.
- ```continue``` → přeskočí zbytek těla a skočí na další iteraci.

```JAVA
for (String jmeno : seznam) {
    if (jmeno.isBlank()) continue; // přeskočí prázdné
    if (jmeno.equals("STOP")) break; // ukončí celý cyklus
    System.out.println(jmeno);
}
```

**Vyhýbej se nekonečným cyklům bez důvodu**
- ```while(true)``` je v pořádku jen pokud máš jasnou **exit podmínku** uvnitř (```break```).


## Vnořené Cykly.

Vnořený cyklus = cyklus uvnitř jiného cyklu.
Každý průchod **vnějšího cyklu** spustí celý **vnitřní cyklus**.

```JAVA
for (int i = 0; i < 3; i++) {       // Vnější cyklus
    for (int j = 0; j < 2; j++) {   // Vnitřní cyklus
        System.out.println(i + "," + j);
    }
}

//Výstup

/*
0,0
0,1
1,0
1,1
2,0
2,1
*/
```

Analogie:

Představ si, že máš dvě **sady úkolů**:

- **Vnější cyklus** = úkoly, které děláš **každý den** (např. 3 dny v týdnu).
- **Vnitřní cyklus** = úkoly, které děláš **každý den ráno** (např. 2 věci).

Jak to probíhá?

- Den 1: ráno uděláš úkol 1, úkol 2.
- Den 2: ráno uděláš úkol 1, úkol 2.
- Den 3: ráno uděláš úkol 1, úkol 2.

Výsledek:

```
Den 1, úkol 1
Den 1, úkol 2
Den 2, úkol 1
Den 2, úkol 2
Den 3, úkol 1
Den 3, úkol 2
```

To je přesně to, co dělá kód:

```JAVA
for (int i = 0; i < 3; i++) {       // 3 dny
    for (int j = 0; j < 2; j++) {   // 2 úkoly každý den
        System.out.println(i + "," + j);
    }
}
```

**Každý prvek vnější sady (dny) spustí celý seznam vnitřních úkolů (ráno).**

Pokud má **vnější cyklus** ```n``` iterací a **vnitřní** ```m``` iterací → celkem ```n × m``` průchodů.

V našem příkladu:

- ```n = 3``` (dny)
- ```m = 2``` (úkoly)
3 × 2 = **6 průchodů**.

Proto se ve výstupu objeví 6 řádků.

**Tipy**

- **Optimalizuj, když můžeš** – často lze vnořený cyklus nahradit datovou strukturou:
    - místo dvojitého hledání → použij ```  HashSet``` pro O(1) lookup.
- **Early exit** – pokud hledáš jen první výsledek, **ukonči cyklus hned**, neprocházej zbytek.


### Časová složitost

Pokud máš:

vnější cyklus ```n``` iterací
vnitřní cyklus ```m``` iterací
- celkový počet kroků = ```n × m```.

Pokud ```n``` a ```m``` jsou stejné (**n**), složitost je:
- **2** cykly → ```O(n²)```
- **3** cykly → ```O(n³)```

Pro malé n (např. n=10) je to v pohodě.
Pro velké n (n=10^6) je to katastrofa – čas roste **násobně**, ne lineárně.

### Jak to optimalizovat

- 1) Nahrazení vnořeného cyklu vhodnou datovou strukturou (hash look-up místo hledání v seznamu)

**Problém (O(n²))**

```JAVA
for (Item a : listA) {
    for (Item b : listB) {
        if (a.id == b.id) {
            // match
        }
    }
}
```

**Řešení (O(n) průměrně): HashSet / HashMap**

```JAVA
Set<Integer> idsB = listB.stream()
        .map(b -> b.id)
        .collect(Collectors.toSet());  // HashSet

for (Item a : listA) {
    if (idsB.contains(a.id)) {
        // match
    }
}
```

**Proč to funguje**: ```contains``` v ```HashSet``` je (průměrně) **O(1)** místo O(n).
**Pozor na**
- Implementuj správně ```equals()``` a ```hashCode()``` u klíčového typu (jinak ```contains``` selže).
- Potřebuješ-li zachovat vložené pořadí, použij ```LinkedHashSet```; pro řazení ```TreeSet```.
- Když je seznam **tříděný**, zvaž **binární hledání** (```Collections.binarySearch```) místo HashSetu.

- 2) Early exit (předčasné ukončení) 
```JAVA
boolean exists = existsMatch(n, m);

boolean existsMatch(int n, int m) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            if (found(i, j)) return true; // early return
        }
    }
    return false;
}
```

- 3) Předpočítání (loop-invariant code motion)

**Špatně (počítáš stejné dokola):**

```JAVA
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        double s = Math.sin(i);   // počítá se m× pro stejné i
        use(s, j);
    }
}
```

**Lépe (vynes ven to, co se nemění vnitřním cyklem):**

```JAVA
for (int i = 0; i < n; i++) {
    double s = Math.sin(i);       // 1× pro každé i
    for (int j = 0; j < m; j++) {
        use(s, j);
    }
}
```