# 🧩 Vytváření, aktualizace a mazání uživatelů

**Správa uživatelských účtů** v systému **Linux** zahrnuje 
**vytváření**, **aktualizaci** a **mazání uživatelů** za účelem 
zajištění **bezpečnosti systému** a **efektivního využití zdrojů**.  

Klíčové příkazy:

```BASH
useradd [uživatel]        # vytvoření nového uživatele
adduser [uživatel]        # alternativní způsob vytvoření uživatele
usermod [parametry] [uživatel]   # aktualizace údajů o uživateli (např. shell, domovský adresář)
userdel [uživatel]        # odstranění uživatele
```

Například pro změnu výchozího shellu uživatele:

```BASH
usermod -s /bin/bash [uživatel]
```

Tato správa je **nezbytná** pro udržování **bezpečného** a **organizovaného prostředí** v systému s **více uživateli** a pro **efektivní alokaci zdrojů**.