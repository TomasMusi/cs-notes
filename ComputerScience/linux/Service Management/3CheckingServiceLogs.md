# 🧾 Kontrola protokolů služeb

Systémové protokoly jsou nezbytné pro **řešení problémů** a **monitorování systémů Linux**.  

Většina protokolů je uložena v adresáři `/var/log` a spravována systémem **systemd**.  

K zobrazení systémových protokolů použijte:

```BASH
journalctl
```

Pro konkrétní protokoly služeb použijte:

```BASH
journalctl -u název_služby
```

Příkaz pro zobrazení zpráv kernelu:

```BASH
dmesg
```

Pravidelné monitorování protokolů je pro **správu systému** zásadní.