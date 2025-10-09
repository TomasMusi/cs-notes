# 🖥️ Monitorování procesů v Linuxu

Linuxové procesy lze monitorovat pomocí virtuálního souborového systému ```proc``` a příkazů jako ```ps```, ```top``` a ```htop```.  

Pro snímky procesů použijte 

```BASH
ps -ef
```

pro zobrazení v reálném čase  

```BASH
top 
# nebo
htop
```

Adresář ```/proc``` obsahuje podrobné informace o procesech.  

Konkrétní podrobnosti o procesech zobrazíte příkazem  

```BASH
cat /proc/{PID}/status
```

Nezbytné pro monitorování výkonu systému a řešení problémů.