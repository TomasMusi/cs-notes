# ⚙️ Řízení úloh v Linuxu

Linux procesy běží na popředí (přímo přijímají vstup od uživatele) nebo na pozadí (běží nezávisle).  

Procesy lze přesunout na pozadí pomocí příkazu  

```BASH
& 
# nebo
bg
```

Na popředí je lze přivést pomocí příkazu:

```BASH
fg
```

Pomocí klávesové zkratky ```Ctrl+Z``` lze proces pozastavit a příkazem  

```BASH
bg # jej obnovit na pozadí.  
```

Jedná se o součást řízení úloh pro správu více úkolů současně z jednoho terminálu.