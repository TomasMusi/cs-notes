# ↔️ Příkaz expand

Příkaz ```expand``` převádí tabulátory na mezery v textových souborech, což je užitečné pro jednotné formátování v různých systémech a editorech.  

Výchozí převod je 8 mezer na tabulátor.  

Pro základní převod použijte:  

```BASH
expand file_name
```

nebo  

```BASH
expand -t 4 file_name
```

pro zadání 4 mezer na tabulátor.  

Nezbytné pro zachování čitelnosti kódu a jednotného odsazení v shellových skriptech.