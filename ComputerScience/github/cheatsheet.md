# STAGE & SNAPSHOT  
### Práce se snapshoty a Git staging area

```bash
git status
# zobrazí změněné soubory v pracovním adresáři, připravené pro další commit

git add [file]
# přidá soubor tak, jak aktuálně vypadá, do dalšího commitu (stage)

git reset [file]
# odstraní soubor ze staging area, ale zachová změny v pracovním adresáři

git diff
# ukáže rozdíly, které jsou změněné, ale nejsou staged

git diff --staged
# ukáže rozdíly, které jsou staged, ale ještě necommitnuté

git commit -m "[descriptive message]"
# commitne staged obsah jako nový snapshot
```

# SETUP

### Nastavení uživatelských informací napříč všemi lokálními repozitáři

```BASH
git config --global user.name "[firstname lastname]"
# nastaví jméno, které bude identifikovatelné v historii commitů

git config --global user.email "[valid-email]"
# nastaví e-mail, který bude přidružen ke každému commit markeru

git config --global color.ui auto
# nastaví automatické barevné zvýraznění pro přehlednost výpisů
```

# BRANCH & MERGE

### Izolace práce v branchích, změna kontextu a slučování změn

```BASH
git branch
# vypíše všechny branche, * označuje aktivní větev

git branch [branch-name]
# vytvoří novou branch na aktuálním commitu

git checkout
# přepne se na jinou branch a načte ji do pracovního adresáře

git merge [branch]
# sloučí historii zadané branche do aktuální

git log
# zobrazí všechny commity v historii aktuální branche
``` 

# SETUP & INIT

### Nastavení uživatele, inicializace a klonování repozitářů

```BASH
git init
# inicializuje existující adresář jako Git repozitář

git clone [url]
# stáhne celý repozitář z hostované lokace přes URL
```

# INSPECT & COMPARE

### Zkoumání logů, rozdílů a informací o objektech

```BASH
git log
# zobrazí historii commitů pro aktuální branch

git log branchB..branchA
# zobrazí commity na branchA, které nejsou na branchB

git log --follow [file]
# zobrazí commity, které změnily daný soubor, i po přejmenování

git diff branchB...branchA
# zobrazí rozdíly mezi obsahem branchA a branchB

git show [SHA]
# zobrazí jakýkoli objekt v Gitu v čitelné podobě
```

# SHARE & UPDATE

### Získávání aktualizací z jiného repozitáře a aktualizace lokální kopie

```BASH
git remote add [alias] [url]
# přidá Git URL jako alias

git fetch [alias]
# stáhne všechny branche z daného Git remote

git merge [alias]/[branch]
# sloučí vzdálenou branch do aktuální pro její aktualizaci

git push [alias] [branch]
# odešle lokální commity na vzdálený repozitář

git pull
# stáhne a sloučí všechny commity z tracking remote branche
```

# TRACKING PATH CHANGES

### Verze změn a mazání cest k souborům

```BASH
git rm [file]
# smaže soubor z projektu a stageuje jeho odstranění pro commit

git mv [existing-path] [new-path]
# změní cestu existujícího souboru a stageuje přesun

git log --stat -M
# zobrazí log commitů s informacemi o přesunutých souborech
```

# REWRITE HISTORY

### Přepisování branchí, aktualizace commitů a čištění historie

```BASH 
git rebase [branch]
# aplikuje commity aktuální branche nad zadanou branch

git reset --hard [commit]
# vymaže staging area a přepíše pracovní strom podle zadaného commitu
```

# TEMPORARY COMMITS

### Dočasné uložení změněných souborů pro přepnutí branchí

```BASH
git stash
# uloží změněné a staged soubory do dočasného úložiště

git stash list
# zobrazí seznam uložených stashů

git stash pop
# obnoví změny z vrcholu stash zásobníku

git stash drop
# odstraní změny z vrcholu stash zásobníku
```