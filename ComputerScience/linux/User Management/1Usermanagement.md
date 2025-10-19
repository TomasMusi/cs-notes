# 👤 Správa uživatelů

**Správa uživatelů** v systému **Linux** umožňuje více uživatelům 
pracovat se systémem **izolovaně**.  

Zahrnuje:
- **vytváření**, **mazání** a **úpravy** uživatelů a skupin  
- **přiřazování oprávnění** a **vlastnictví souborů**  

Klíčové příkazy:

```BASH
adduser [uživatel]      # vytvoření nového uživatele
useradd [uživatel]      # alternativní způsob vytvoření uživatele
deluser [uživatel]      # odstranění uživatele
userdel [uživatel]      # alternativní způsob odstranění uživatele
passwd [uživatel]       # správa hesla uživatele
su [uživatel]           # přepnutí na jiného uživatele
```

Správa uživatelů je **nezbytná** pro zajištění správné **přístupnosti** a udržování **bezpečnosti systému Linux**.