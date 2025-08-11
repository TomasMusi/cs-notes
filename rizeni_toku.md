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