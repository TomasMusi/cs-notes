# Inicializace git repozitáře v adresáři

```BASH
git init # Inicializuje repozitář.
```

## Přidání souborů

K přidání souborů používáme git add file1 file2

```BASH
git add file1 file2 # přidá soubory do staging area, fáze, kde je navrhujeme k dalšímu commitu.
```

Pokud je vše v pořádku, použijeme commit příkaz pro trvalé uložení snapshotu do repozitáře, společně se smysluplnou zprávou, která popisuje, co commit představuje.

```BASH
git commit -m "Initial commit" # commit se zprávou.
```

Toto je velmi důležité pro přehlednou historii.

## COMMITS

Každý commit v našem repozitáři obsahuje jedinečný identifikátor generovaný gitem.
Každý commit obsahuje také informace o tom, co se změnilo — datum/čas, autora a kompletní snapshot.

Příkaz git status nám řekne, v jaké fázi se nacházíme.

```BASH
git status # ukazuje stav adresáře a staging area.
```

## Odstranění souboru z gitu

```BASH
# odstranění souboru pomocí unixového příkazu
rm file2.txt # odstraní soubor

# nyní, když zkontrolujeme stav v gitu, uvidíme, že soubor byl smazán z pracovního adresáře, ale stále existuje ve staging area
git status # uvidíme smazaný soubor

# ověříme, že je stále ve staging area
git ls-files

file1.txt 
file2.txt

# k úplnému odstranění musíme provést
git add file2.txt # nyní je odstraněn.
```

## Přejmenování nebo přesun souboru

```BASH
git mv main.js file1.js # oba soubory jsou změněny v pracovním adresáři i ve staging area.
```

## Ignorování souborů, které nechceme sledovat

```BASH
git add .gitignore
```


## Zjednodušený výpis stavu

```BASH
git status -s

# dává nám dva sloupce, levý představuje staging area a pravý pracovní adresář
```

## Kontrola změn před commitem

Před commitem bychom měli zkontrolovat kód, abychom do repozitáře necommitovali chybný kód.
Příkaz ```git status``` ukazuje pouze soubory, které byly ovlivněny.

Zde vidíme:
```BASH
git status -s 

# M     file1.js
# A     file2.js
```

Pokud chceme vidět přesné řádky kódu, které jsme staged, použijeme:

```BASH
git diff --staged 
```

## Zobrazení historie commitů

```BASH
git log
git log --oneline # zkrácená verze
```

Můžeme si také zobrazit konkrétní commit podle ID:

```BASH
git show b27e1d4
```

## Odebrání souboru ze staging area

```BASH
git restore --staged file1.js
```

## Obnovení souboru do dřívější verze

```BASH
# odstranění souboru pro test
git rm file1.js 

# kontrola, zda byl smazán
git status -s 

# vytvoření commitu
git commit -m "Delete file1.js"

# kontrola historie
git log --oneline 

# obnovení souboru z dřívějšího commitu
git restore --source=b27e1d4 file.js
```

## Další užitečné příkazy

``` BASH
git add *.txt # přidá všechny .txt soubory
git add *.js # přidá všechny .js soubory
git add . # přidá všechny soubory
```