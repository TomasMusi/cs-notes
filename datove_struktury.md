# Základní myšlenka datových struktur

- Datová struktura = **konkrétní způsob organizace a uložení dat v paměti** tak, aby určité operace (vyhledávání, vkládání, mazání, třídění) byly **rychlé** a **predikovatelné**.

    - **Čtu často, málo přidávám** → Array / HashMap

    - **Často vkládám uprostřed** → Linked List

    - **Potřebuju prioritizaci** → Heap

    - **Potřebuju setříděnost + rychlé hledání** → Balanced Tree

    - **Potřebuju pouze unikátní prvky** → Set

## Asymptotika (Big-O) a co znamená v reálu

Teorie:

- **O(1)** – konstantní čas, nezávisí na velikosti dat

- **O(log n)** – velikost vstupu se zmenšuje exponenciálně po každém kroku. Logaritmická složitost znamená, že při každém kroku zredukuješ prostor hledání o konstantní násobek (často na polovinu – binární vyhledávání).

- **O(n)** – lineární čas, musíš projít všechno

- **O(n log n)** – typické pro třídicí algoritmy

- **O(n²)** – špatné pro velká data. Typicky se objevuje u naivních třídicích algoritmů (bubble sort, insertion sort bez optimalizací) nebo u algoritmů, které porovnávají každý prvek s každým.

Praxe:

- **Malé n** → i „pomalejší“ algoritmus může být rychlejší kvůli menší konstantě

- **Velké n** → špatná asymptotika tě zabije, i když má malou konstantu

- **Cache locality** může z O(n) udělat v reálu *rychlejší* než O(log n) (např. hledání v setříděném poli vs. v stromu)

## Paměťová architektura a cache

Co je CPU cache a proč existuje?

- **RAM** je hlavní paměť počítače. Je velká (gigabajty), ale pro procesor relativně **pomalá**.
- **CPU cache** je malá (jen pár MB), ale extrémně **rychlá** paměť uvnitř procesoru. Procesor ji používá jako **rychlý sklad na věci, které bude potřebovat hned**.
- Myšlenka je: když CPU potřebuje data, je lepší, aby už je měl připravené v cache, než aby si je musel jít načíst z pomalé RAM.

Co je „cache line“?

- Cache není uložena po jednotlivých bajtech, ale po **blocích** pevné velikosti.
- Každý takový blok se jmenuje **cache line**. Typicky má **64 bajtů** (což je tak 16 čísel typu ```int``` za sebou, pokud má ```int``` 4 bajty).
- Když procesor potřebuje jeden prvek z paměti, načte **celý blok**, ve kterém se prvek nachází. To znamená: když pak potřebuje sousední prvky, už je má připravené → **rychlejší přístup**.

Locality – co to znamená?

Locality je míra toho, **jak blízko u sebe jsou data, ke kterým CPU přistupuje.**

Existují dva druhy:

- **Spatial locality** (*prostorová*) → přistupuješ k datům, která leží blízko u sebe v paměti  → CPU načte jeden blok a využije z něj co nejvíce dat, než musí pro další blok do RAM.
    - Přistupuješ k **datům, která jsou blízko sebe v paměti**.
    - Příklad:
        - Máš pole (```array```) v paměti uložené souvisle: ```[1, 2, 3, 4, 5]```
        - CPU načte ```[1, 2, 3, 4, 5]``` jedním nebo dvěma tahy
        - Sekvenční průchod polem = téměř optimální pro cache

- **Temporal locality** (*časová*) → opakovaně přistupuješ ke stejným datům  → CPU je drží v cache, takže je má okamžitě k dispozici. Opakované přístupy ke stejnému indexu v poli při vícenásobném průchodu.
    - Přistupuješ k **těm samým datům opakovaně** v krátkém čase.
    - CPU si data nechá v cache, takže druhý přístup je extrémně rychlý.

### Proč může být O(n) rychlejší než O(log n)

Teoretická složitost nepočítá **čas přístupu k paměti** — počítá jen počet operací.

Příklad:

- **Hledání v setříděném poli** (```array```):
    - Binary search → O(log n)
    - Lineární průchod → O(n)
    - Ale… pokud pole leží souvisle v paměti, procesor načítá bloky dopředu a téměř všechna data má „po ruce“  → jeden „miss“ načte spoustu dalších prvků.

- **Hledání v binárním stromu**:
    - O(log n) teoreticky
    - Ale každý uzel je v paměti někde jinde (díky pointerům)
    - Skáčeš po RAM, cache miss skoro u každého kroku → reálně mnohem pomalejší než lineární průchod polem

O(n) sekvenční čtení pole < O(log n) hledání v stromu
(v reálném čase, ne v Big-O matematice)

