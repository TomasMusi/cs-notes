# 🔐 Práva a oprávnění v Linuxu

- V systémech Linux jsou práva a oprávnění přiřazována souborům a adresářům ve formě oprávnění.  
- Tato oprávnění určují, kdo je může číst, zapisovat nebo spouštět (provádět).  
- V systému Linux existují tři typy uživatelů: vlastníci, skupiny a ostatní, kteří mohou mít různá oprávnění.  

- Ve skutečnosti mají oprávnění v systému svůj důvod: zabránit neoprávněným uživatelům provádět změny v systému, které by nakonec ovlivnily ostatní uživatele.  
- S nedostatečnými oprávněními mohou neoprávnění uživatelé provádět změny, které by byly pro systém Linux prospěšné nebo neškodné.  

- Podívejme se na příklad:

```bash
-rwxr--r-- 1 root root 4096 Jan 1 12:00 filename
```

- Z výše uvedeného příkladu vyplývá, že první znak - označuje, zda se jedná o běžný soubor (-) nebo adresář (d).

- Následující skupina tří znaků (rwx) představuje oprávnění pro vlastníka souboru.

- Další tři znaky (r--) představují oprávnění pro skupinu a poslední skupina tří znaků (r--) představuje oprávnění pro ostatní.

- Znak ```r``` označuje, že soubor lze číst, znak ```w``` označuje, že do souboru lze zapisovat, a znak ```x``` označuje, že soubor lze spustit.

- Oprávnění lze změnit pomocí příkazů ```chmod```, ```chown``` a ```chgrp```.