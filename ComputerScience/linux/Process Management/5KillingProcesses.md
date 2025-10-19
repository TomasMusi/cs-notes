# 🔪 Ukončování procesů

Příkaz **kill** ukončuje procesy v systému **Linux** zasláním signálů konkrétním 
identifikátorům procesů (**PID**).  

K ručnímu ukončení procesů použijte:

```BASH
kill [signál] PID
```

Různé signály poskytují různé metody ukončení:

- ```SIGTERM``` - šetrné ukončení procesu
- ```SIGKILL``` - násilné ukončení procesu

Ukončení procesu je **nezbytné** pro správu **nereagujících** nebo **nežádoucích procesů**.