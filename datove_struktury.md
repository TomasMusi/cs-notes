# Základní myšlenka datových struktur

- Datová struktura = **konkrétní způsob organizace a uložení dat v paměti** tak, aby určité operace (vyhledávání, vkládání, mazání, třídění) byly **rychlé** a **predikovatelné**.

    - **Čtu často, málo přidávám** → Array / HashMap

    - **Často vkládám uprostřed** → Linked List

    - **Potřebuju prioritizaci** → Heap

    - **Potřebuju setříděnost + rychlé hledání** → Balanced Tree

    - **Potřebuju pouze unikátní prvky** → Set


## Checklist, při výběru Datové Struktury

- 1. **Jaký je mix operací?**
    - Kolik % čtení, vkládání, mazání, iterací, range queries?
    - Optimalizuj pro nejčastější operace.

- 2. **Potřebuju pořadí nebo řazení?**
    - Ano → vyvážený strom (```TreeMap/TreeSet```)
    - Ne → hash (```HashMap/HashSet```)

- 3. **Jak velké je n?**
    - Malé → jednoduchost a cache locality jsou důležitější než Big-O
    - Velké → asymptotika (O(log n) vs O(n)) rozhoduje víc

- 4. **Cache locality**
    - Sekvenční přístup? → pole / array-based struktura
    - Náhodný přístup / pointer chasing? → pozor na linked listy a nevyvážené stromy
        - Náhodný přístup = skáčeš po paměti na náhodná místa.
        - **Pointer chasing** = máš ukazatel na další prvek (např. linked list, strom) a musíš ho načíst, abys věděl, kde jsou další data.
        - Problém:
            - Každý skok může skočit do úplně jiné části RAM.
            - Každý takový skok = **cache miss** → CPU musí čekat na RAM (desítky až stovky ns).
            - Při průchodu linked listu máš téměř **cache miss na každém prvku**.

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

## Datové Struktury

**1. Array (Pole)**

> *Představ si školní chodbu se skříňkami – každá má své číslo (index) a pevné místo.*

**Popis**: Souvislý blok paměti, kde jsou prvky uloženy **sekvenčně** jeden za druhým.  
Každý prvek má svůj index, což umožňuje extrémně rychlý přístup.

**Výhody:**
- **O(1)** přístup k prvku podle indexu.
- Výborná **cache locality** (sekvenční data → vysoký hit rate).
- Jednoduchá implementace.
- Dobré pro sekvenční procházení.

**Nevýhody:**
- Pevná velikost (u statických polí).
- Vložení/mazání uprostřed = **O(n)** kvůli posunu prvků.
- Pokud je pole plné, je nutné vytvořit nové a zkopírovat všechny prvky (**O(n)**).

**Příklad:**
```text
Původní pole: [1, 2, 3]
Nové pole po přidání 4: [1, 2, 3, 4]
```

**Cache locality**: vysoká (prvky za sebou v paměti).
**Kdy vybrat**: Když čteš často, málo měníš a potřebuješ rychlý indexový přístup.

**2. Dynamic Array (Vector / ArrayList)**

**Popis**: Pole, které se při zaplnění zvětší.

**Výhody:**

- O(1) průměrný čas pro přidání na konec (občasná drahá operace zvětšení pole se rozloží mezi všechny vložení).
- Vysoká cache locality.
- Snadné iterace.

**Nevýhody:**

- drahý resize (kopírování O(n)).
- Stále O(n) pro vložení/mazání uprostřed.

**Cache locality**: vysoká.
**Kdy vybrat**: Když potřebuješ dynamický růst, ale pořád primárně čteš a iteruješ.


**3. Linked List**

> *Představ si vlak, kde musíš projít každý vagon, než najdeš ten správný.*

**Popis**: Každý prvek (**uzel**) obsahuje hodnotu a ukazatel (*pointer*) na další (případně předchozí) prvek. Může být **singly linked** (ukazatel jen vpřed) nebo **doubly linked** (ukazatel vpřed i zpět).  


**Výhody:**

- **O(1)** vložení/mazání uprostřed, pokud máš pointer na dané místo.
- Flexibilní velikost (není třeba předem znát počet prvků).
- Jednoduché spojování a rozdělování seznamů.

**Nevýhody:**

- **O(n)** přístup podle indexu (musíš projít všechny předchozí prvky).
- Vysoký paměťový overhead (ukazatele zabírají místo navíc).
- Špatná **cache locality** (pointer chasing → nízký hit rate), pokud uzly nejsou alokovány sekvenčně.
- Časté alokace mohou fragmentovat paměť.

**Cache locality**: nízká.
**Kdy vybrat**: Jen pokud často vkládáš/mažeš uprostřed a nepotřebuješ rychlou indexaci.

**4. Stack**

> *Jako věž z chipsů – poslední chips položený navrch bude první, který sníš.*

**Popis**: LIFO struktura (*Last In, First Out*), kde poslední vložený prvek je první, který se odebere.  

**Výhody:**

- **O(1)** pro přidání (```push```) a odebrání (```pop```)..
- Snadná implementace nad array nebo linked listem.
- Dobrá locality, pokud array-based.

**Nevýhody:**
- Přístup jen k poslednímu prvku.
- Nepodporuje přímé vyhledávání.

**Cache locality**: vysoká (array-based).
**Kdy vybrat:**  
- Undo/redo operace.  
- Rekurze (volací zásobník).  
- Backtracking algoritmy (např. DFS).

**5. Queue (Fronta)**

> *Řada u pokladny – kdo přijde první, ten jde první.*

**Popis**: FIFO struktura (*First In, First Out*), kde se nové prvky přidávají na konec a odebírají z začátku.  


**Výhody:**

- **O(1)** pro přidání (`enqueue`) a odebrání (`dequeue`) při správné implementaci.
- Jednoduchá implementace nad kruhovým bufferem.
- Dobrá **cache locality** u array-based verze.

**Nevýhody**

- Přístup pouze k prvnímu a poslednímu prvku.
- Linked list implementace má špatnou cache locality (pointer chasing).
- Nelze libovolně přistupovat k prvkům podle indexu jako u pole.    

**Cache locality** dobrá u kruhového bufferu, špatná u linked listu
**Kdy vybrat** Pro plánování úloh, streamy, BFS.

**6. Deque**

**Popis:** Double-ended queue (přidávání/mazání na obou koncích).

**Výhody:**

- O(1) pro operace na obou koncích.
- Dobrá locality u blokových implementací.

**Nevýhody**

- O(n) pro vložení uprostřed
- Mírně větší paměťový overhead než array.

**Cache Locality** super u blokové implementace
**Kdy vybrat** Když potřebuješ efektivní operace na začátku i konci.

**7. HashMap/ HashSet**

> *Představ si kancelář, kde má každý zaměstnanec svoji poštovní schránku s číslem.  
> Když přijde dopis pro Johna, místo procházení všech schránek víš rovnou, že John má schránku č. 4.  
> Sally má schránku č. 5. Každý přesně ví, kam co patří.*

**Popis:** HashMap (klíč–hodnota) a HashSet (unikátní prvky) ukládají data podle výsledku **hashovací funkce**.  
Hashovací funkce převádí klíč na index v interním poli (bucket array), což umožňuje extrémně rychlý přístup k datům. Ukládá klíč–hodnota páry podle hashovací funkce.

**Výhody:**

- **O(1)** průměrná složitost pro vyhledání, vložení i mazání.
- Skvělé pro velké množství lookupů.
- HashSet zaručuje unikátnost prvků.

**Nevýhody:**

- Možnost kolizí (v nejhorším případě až O(n), moderní implementace často degradují jen na O(log n) díky přepnutí na stromovou strukturu).
- Neudržuje pořadí (výjimkou jsou ordered hash mapy).
- Vyšší paměťová náročnost (volné sloty v bucket array).

**Hashovací kolize – co když dvě osoby chtějí stejnou schránku?**  
> *Představ si, že přijde nový zaměstnanec Andy. Jméno „Andy“ má stejně jako „John“ čtyři písmena.  
> Pokud by hashovací funkce určovala číslo schránky podle délky jména, oba by skončili na pozici č. 4.*

Kolize nastává, když různé klíče směřují na stejnou pozici v interním poli.  
Řešení kolizí:
- **Řetězení (chaining)** – v jednom bucketu je uložený seznam (např. linked list) všech prvků se stejným indexem.
- **Open addressing (lineární prohledávání, kvadratické prohledávání, double hashing)** – pokud je bucket obsazen, hledá se jiný volný slot.

**Cache locality**: super při open addressing, špatná při chainingu.
**Kdy vybrat**: Rychlý přístup podle klíče, nezáleží na pořadí.

**8. Balanced BST (AVL, Red-Black Tree, TreeMap/TreeSet)**

**Popis**: Strom udržující rovnováhu pro O(log n) operace.

**Výhody:**

- Pořadí udržováno automaticky.
- Rychlé range queries.
- Stabilní výkon v nejhorším případě.

**Nevýhody:**

- Větší konstanty než hash mapy.
- Horší cache locality (pointer chasing).

**Cache Locality:** střední až nízka (ukazatele)
**Kdy vybrat:** Když potřebuješ řazení, rozsahy, stabilní výkon.

**9. Heap (Priority Queue)**

> *Představ si pyramidu z krabic, kde nahoře je vždy ta s nejvyšší nebo nejnižší prioritou.*  
> - **Min Heap**: rodič < děti  
> - **Max Heap**: rodič > děti

**Popis:** Vyvážený binární strom uložený v poli (array-based), kde prvek na vrcholu (*root*) má vždy nejvyšší (u max heap) nebo nejnižší (u min heap) prioritu.  
Indexování v poli umožňuje efektivní nalezení rodičů i dětí bez pointerů, což zlepšuje cache locality.

**Výhody:**

- **O(1)** přístup k prvku s nejvyšší prioritou (*root*).
- **O(log n)** vložení a odebrání díky přeuspořádání (*heapify*) stromu při zachování heap property.

**Nevýhody:**

- Heap: Je částečně uspořádaný podle heap property (rodič ≤/≥ děti), ale není plně setříděný.
- Přístup k jinému prvku než *root* = **O(n)**.
- Nehodí se pro časté vyhledávání libovolného prvku.

**Cache locality** Dobrá (array-based).
**Kdy vybrat** Plánovače úloh, algoritmy s prioritou (Dijkstra). Situace, kdy potřebuješ často přidávat/odebírat prvky s nejvyšší prioritou. EOF

**10. Trie (Prefix Tree)**

**Popis:** Strom, kde cesta od kořene odpovídá prefixu klíče.

**Výhody:**

- Rychlé vyhledávání podle prefixu.
- Nezávislé na délce klíče při hledání.

**Nevýhody:**

- Velká paměťová náročnost (spousta pointerů).
- Špatná cache locality.

**Cache locality:** nízká.
**Kdy vybrat:** Autocomplete, IP routing.

**11. B-Tree / B+ Tree**

**Popis** Strom optimalizovaný pro blokový přístup (disk / velké cache lines).

**Výhody:**

- Méně přístupů k paměti/disku (uzly obsahují více klíčů).
- Skvělé pro databáze a indexy.

**Nevýhody**

- Složitější implementace.
- Větší uzly → dražší úpravy.

**Cache locality:** velmi dobrá (blokové načítání).
**Kdy vybrat:** Databázové indexy, souborové systémy.