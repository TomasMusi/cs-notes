# Krok 1: Stáhnout docker

Je potřeba stáhnout docker, abycho ho mohli využívat.

```BASH
sudo pacman -S docker ## Na Arch Linuxu
```

Kontrola naši verze dockeru:

```Bash
docker -v ## Prikaz nam da verzi dockeru.
```

# Krok: 2 Setupnout Docker v našem IDE.

Pokud využíváme VS Code, musíme stáhnout extension, abychom měli language support

# Krok: 3 Docker File 

Co je to docker file? Kdyz si vzpomeneme na naši analogií s receptem, tak tohle je přesně místo kde píšeme náš recept.

Tudíž pokud bychom chtěli spustit náš program (jednoduchý node sever, vypadalo by ot nějak takhle: )
```BASH
# Uses node version 22 as our base image
FROM node:22

# Goes to the app directory (think of it like a cd terminal command)
WORKDIR /app

# Copy package.json and package-lock.json (if available)
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the rest of our app into the container (Copies everything so make sure to have dockerignore)
COPY ..

# Set port enviroment variable (because we dont share the .env)
ENV PORT=9000

# Expose the port so our computer can access it.
EXPOSE 9000

# Run the app
CMD ["npm", "start"]
```

**Důležitá poznámka** Docker je velmi chytrý, využívá Technologii Layer Caching. Tudíž každý krok, který jsme vypsali tak se bere jako layer. A docker se dívá na každý layer inviduálně, což se překládá...

**layer changed** = do it again (rebuild it). 
**layer DID not change** = use cache. 

# Krok: 4 Building the Image

Abychom buildnuli náš Image musíme využít terminál

```BASH
docker build -t terrible_docker_example . 
# -t <název jak chceme aby se image jmenoval>
# . Místo kam chceme uložit náš image.
```

# Krok: 5 Running the Container

```BASH
docker run -p 9000:9000 terrible_docker_example

# -p 9000:9000, je tzv. Port Forwarding, ve zkratce most mezi Containerem a našim počítačem. 
# terrible_docker_example je název našeho buildnutého Image. který jsme udělali.
```

# Krok: 6 Debugging

Docker nám nezabraňuje psát špatný kod, tudíž existuje i debugging, který je poměrně dosti přehledný, existuje GUI i terminal verze.

# Krok: 7 Docker Scout

Co je to Docker Scout? Je to nástroj vytvořen Dockerem, který se dívá dovnitř Docker Image a generuje to detailovaný report všech packages, které jsou uvnitř image. Kouká se na všechny zranitelnosti uvnitř těchto packages, jestli to detekuje některé zranitelnosti, doporučí to jak je handlnout.

# Krok: 8: Docker Compose & Docker Volumes

Náš předešlý jednoduchý příklad s Node.js byl velmi primitivní, co dělat když máme Backend, Databazi, Frontend?

Je možné tohle všechno nakombinovat do jednoho obrovského containeru... ale to bych nedoporučoval. 

Tudíž je lepší tyto servisy, rozdělit a dát je do jejich vlastních Containerů, tohle se nazývá **Multi Container Application**, avšak tohle vytváří nový problém. Tím, že mám více containerů musíme tyto containery spustit odděleně a musíme najít způsob jak je propojit. Ale!!!!! Máme řešení **Docker Compose**. Docker compose říká všem našim containerům jak mají mezi sebou spolupracovat. 

Tudíž si ukážeme jak vytvořit Compose kde budeme mít node server a DB.

vytvoříme soubor s názvem ``compose.yaml``

```BASH
# Uvnitř Compose.yaml vytvoříme object zvaný services:
# Dále budeme vytvářet keys, které reprezentují containery, které chceme spustit. 
services: 
    # Kvůli tomu, že náš backend je již dávno vygenerován pomocí Docker File, dáme tam pouze jeho umístění
    backend:
        build: .
        # Náš backend potřebuje Port Forwarding.
        ports:
            - '9000:9000'
    db: 
    # zde využijeme image key, protože nevyužíváme Docker File, pro tuhle DB.
        image: postgres:latest
        environment:
            POSTGRES_USER: user
            POSTGRES_PASSWORD: pass
            POSTGRES_DB: mydb
        # Musíme ještě přidat poslední věc. Docker Volumes, kdykoliv vypneme naše containery, ztratíme state a data a nyní naše  containery nesdílí data mezi sebou. Tudíž musíme přidat Docker Volume. Volume je zjednodušeně řečeno složka v našem počítači, kterou si docker může zpřístupnit, aby mohla uložit jakékoliv data z našich containerů
        volumes:
            - postgres_data:/var/lib/postgresql/data
volumes:
# toto říká: Hey docker vytvoř volume, zvanou postgres_data
    postgres_data
```

Nyní když tohle máme stačí napsat

```BASH
docker compose up
```

Pokud bychom to chtěli vypnout tak uděláme jednoduchý příkaz

```BASH
docker compose down
```

# Krok: 9 Docker Build Cloud

Už jsme si všimli toho, že building našich containerů zabírá poměrně čas, nyní si můžeme představit jak dlouho to bude trvat při complexních aplikacích. Podle článku většina developerů čeká průměrně hodinu než se to buildne. Proto Docker přišel s Docker Build Cloud, což znamená že se nám naše containery buildují na cloudu. 