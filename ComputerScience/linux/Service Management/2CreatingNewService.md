# 📊 Service Status (Stav služby)

Stav služby zobrazuje aktuální stav služeb **Linuxu**, včetně síťových procesů, 
backendových serverů a aplikací na pozadí.  

Pomocí příkazu:

```BASH
systemctl status service_name
```

můžete zkontrolovat stav služeb prostřednictvím správce **systemd**.

```BASH
systemctl status apache2.service # zobrazí stav webového serveru Apache.
```

Nezbytné pro **diagnostiku problémů, udržování výkonu** a **prevenci výpadků služeb**.