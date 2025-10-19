# ▶️ Spouštění / zastavování služeb

Správa služeb v systému **Linux** řídí systémové služby, jako jsou **firewall**, **síť** a **databáze**, 
pomocí příkazů **systemctl**.  

Základní operace:

```BASH
sudo systemctl start název_služby     # spuštění
sudo systemctl stop název_služby      # zastavení
sudo systemctl restart název_služby   # restart
```

Vyžadují se **oprávnění root**.

Nezbytné pro **správce systému**, kteří spravují **aktualizace** a **změny konfigurace**.