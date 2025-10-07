
# Archivace Dat

- Linux nabízí mocné nástroje pro archivaci, kde se více souborů a adresářů spojí do jednoho souboru, především pro zálohování a zjednodušení distribuce. Hlavní nástroje používané pro tento účel jsou tar, gzip a bzip2.

- Příkaz tar, je univerzální nástroj, který dokáže spravovat a organizovat soubory do jednoho archivu. Gzip a bzip2 se mezitím používají pro kompresi souborů, čímž se zmenšuje velikost souborů a usnadňuje přenos dat.

Podívejte se na následující příkazy v praxi:
```BASH
# Vytvoření archivu tar:
tar cvf archive_name.tar directory_to_archive/

# Rozbalení archivu tar:
tar xvf archive_name.tar

# Vytvoření archivu tar komprimovaného pomocí gzip:
tar cvzf archive_name.tar.gz directory_to_archive/

#Vytvoření archivu tar komprimovaného pomocí bzip2:
tar cvjf archive_name.tar.bz2 directory_to_archive/
```

- Pamatujte, že v systému Linux jsou archivace a komprese samostatné procesy, proto se k archivaci používá tar a ke kompresi gzip/bzip2. Ačkoli se běžně používají společně, lze je podle požadavků použít i samostatně.

