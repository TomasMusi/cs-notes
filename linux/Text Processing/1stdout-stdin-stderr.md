# 📤 Stdout, Stdin a Stderr

Procesy v systému Linux používají tři standardní datové toky: **STDIN** (vstup), **STDOUT** (výstup) a **STDERR** (chybové zprávy).  

**STDOUT** zpracovává normální výstup příkazů, zatímco **STDERR** zpracovává konkrétně chybové zprávy.  

Tyto toky můžete přesměrovat pomocí operátorů, jako je:

```BASH
>   # pro stdout  
2>  # pro stderr
```

To umožňuje oddělené zpracování normálního výstupu a chyb pro lepší skriptování a debugging.