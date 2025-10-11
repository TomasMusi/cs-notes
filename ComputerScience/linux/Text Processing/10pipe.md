# 🔧 Pipe (|)

Pipe (|) je výkonná funkce v systému Linux, která slouží ke spojení dvou nebo více příkazů.  

Tento mechanismus umožňuje, aby výstup jednoho příkazu byl „přesměrován/piped“ jako vstup do jiného příkazu.  

V souvislosti se zpracováním textu je použití pipe obzvláště užitečné, protože umožňuje manipulovat, analyzovat a transformovat textová data bez nutnosti vytvářet zprostředkující soubory nebo programy.  

Zde je jednoduchý příklad propojení/piping dvou příkazů, ls a grep, pro zobrazení seznamu všech textových souborů v aktuálním adresáři:

```BASH
ls | grep '\.txt$'
```

V tomto příkladu příkaz ```ls``` vypíše soubory v aktuálním adresáři a příkaz ```grep``` ```'\.txt$‘``` odfiltruje všechny soubory, které nekončí příponou ```.txt```.  

Příkaz pipe, ```|```, vezme výstup z příkazu ```ls``` a použije jej jako vstup pro příkaz ```grep``` ```'\.txt$‘```.  

Výstupem celého příkazu je seznam textových souborů v aktuálním adresáři.