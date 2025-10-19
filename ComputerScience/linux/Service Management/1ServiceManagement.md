# ⚙️ Správa služeb

Správa služeb řídí služby **Linuxu** („daemons“) během procesů **bootování** a **shutdownu**.  

Mezi běžné příkazy **systemctl** patří:  
start, stop, restart, reload, status, enable/disable.  

Moderní Linux používá **systemd**, zatímco starší systémy používají **SystemV** nebo **Upstart**.  

Příklad:

```BASH
sudo systemctl start sshd # zapne SSH service.
```

Nezbytná dovednost pro **správu systému Linux** a udržování **bezpečných a stabilních systémů**.