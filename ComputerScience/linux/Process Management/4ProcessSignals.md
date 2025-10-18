# ⚙️ Procesní signály v Linuxu

Procesní signály jsou komunikační mechanismy v systému **Linux**, které informují procesy o **synchronních** nebo **asynchronních** událostech.

Mezi běžné signály patří:

- ```SIGINT``` – přerušení procesu
- ```SIGSTOP``` – pozastavení procesu
- ```SIGKILL``` – ukončení procesu

Pro pozastavení konkrétního procesu použijte

```BASH
kill -SIGSTOP 12345
```

Tento příkaz pozastaví proces s **PID** **12345**, dokud není přijat signál ```SIGCONT```.

Nezbytné pro **komplexní správu procesů** a **alokaci systémových zdrojů**.