# 👥 Uživatelé a skupiny

Správa uživatelů v systému **Linux** využívá **skupiny** k efektivní organizaci uživatelů 
a správě oprávnění.  

Skupiny jsou sdružení uživatelů, která zjednodušují správu systému tím, 
že řídí přístup k prostředkům, jako jsou soubory a adresáře.  

Uživatelé mohou patřit do více skupin, což umožňuje přesnou správu oprávnění.  

Příkazy jako:

```BASH
groupadd [skupina]
groupdel [skupina]
groupmod [parametry] [skupina]
usermod -aG [skupina] [uživatel]
gpasswd [parametry] [skupina]
```

umožňují efektivní správu skupin.

Správná správa skupin je zásadní pro **bezpečné** a **organizované systémové prostředí**.