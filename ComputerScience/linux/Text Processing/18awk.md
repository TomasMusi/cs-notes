# ⚙️ Příkaz awk

```awk``` je výkonný text-processing jazyk pro systémy typu Unix, pojmenovaný podle svých tvůrců Aho, Weinberger a Kernighan.  

Čte soubory řádek po řádku, identifikuje vzory a provádí akce na shodách.  

Běžně se používá v bash skriptech pro třídění, filtrování a generování reportů.  

Příklad:  

```BASH
awk '{print $1,$2}' filename
```

vytiskne první dvě pole každého řádku.