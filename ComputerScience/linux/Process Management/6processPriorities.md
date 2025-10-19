# 🎚️ Priority procesů

**Linux** přiřazuje procesům úrovně **priority**, které ovlivňují dobu provedení 
a přidělování systémových zdrojů.  

Priority procesů používají hodnoty **„nice“** v rozmezí od **-20 (nejvyšší priorita)** 
do **+19 (nejnižší priorita)**.  
Pouze uživatel **root** může nastavit **zápornou hodnotu nice**.  

Souborový systém `/proc` obsahuje informace o procesech, včetně jejich priorit.  

Pro zobrazení priorit procesů použijte:

```BASH
ps -eo pid,pri,user,comm
```

Pro změnu priority existujícího procesu použijte:

```BASH
renice [hodnota] -p [PID]
```

Správná správa priorit je klíčová pro **efektivní alokaci zdrojů** a **optimální výkon systému**.