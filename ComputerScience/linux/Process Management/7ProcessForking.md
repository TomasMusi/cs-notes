# 🌱 Forkování procesů

**Forkování procesů** využívá systémové volání **fork()** k vytvoření 
**podřízených procesů (child processes)** z procesů **nadřazených (parent processes)**, 
což umožňuje **souběžné provádění**.  

Podřízené procesy jsou téměř dokonalými kopiemi svých nadřazených procesů, 
ale mají **odlišné PID**.  
Změny provedené v podřízených procesech **neovlivňují** procesy nadřazené.  

Příklad vytvoření podřízeného procesu v jazyce C:

```C
pid_t pid = fork();
if (pid == 0) {
    // Kód podřízeného procesu
} else if (pid > 0) {
    // Kód nadřazeného procesu
}
```

Forkování je **nezbytné** pro pochopení **vytváření a řízení procesů** v systému **Linux** v prostředí s **více procesy**.