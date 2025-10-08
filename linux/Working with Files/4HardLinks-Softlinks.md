# 🔗 Odkazy na soubory v Linuxu

Linux podporuje dva typy odkazů na soubory.  

**Pevné odkazy** sdílejí stejný inode a data jako původní soubor – pokud je původní soubor smazán, data zůstávají přístupná.  

**Měkké odkazy (symbolické odkazy)** jsou zkratky odkazující na původní cestu k souboru – pokud je původní soubor odstraněn, přestanou fungovat.  

Pevné odkazy se vytvářejí pomocí příkazu:

```BASH
ln
```

Měkké odkazy se vytvářejí pomocí příkazu:

```BASH
ln -s
```

