# 🔐 Autentizační protokoly v systému Linux

Autentizační protokoly v systému Linux zaznamenávají všechny události související s autentizací, jako jsou přihlášení, změny hesel a příkazy ```sudo```.  

Tyto protokoly, které se nacházejí v adresáři ```/var/log/auth.log``` (Debian) nebo ```/var/log/secure``` (RHEL/CentOS), pomáhají odhalit bruteforce útoky a neoprávněné pokusy o přístup.  

Pomocí příkazu ```tail /var/log/auth.log``` můžete zobrazit poslední záznamy.  

Pravidelná analýza protokolů je nezbytná pro monitorování bezpečnosti serveru.  

Zde je příklad, jak můžete pomocí příkazu ```tail``` zobrazit posledních několik záznamů protokolu ověřování:  