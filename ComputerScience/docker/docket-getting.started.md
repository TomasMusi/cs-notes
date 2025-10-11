# Co je to Docker?

- Otevřená platforma, pro vývoj, distribuci a provoz aplikací.
- Umožňuje oddělit aplikace od infrastruktury, což nám umožní software dodávat rychleji.
- Zkracuje dobu mezi napsáním kodu a jeho spuštěním v produkčním prostředí.
- **Zlehčuje process sdílení kodu.**

## Platforma Docker

- Umožňuje spouštět aplikace ve volně izolovaném prostředí zvaném **kontejner**
- Kontejnery jsou lehké a obsahují vše potřebné ke spuštění aplikace, tudíž se nemusíme spoléhat na to, co je nainstalováno na hostitelovi.
- Kontejnery můžeme sdílet během práce a mít jistotu, že všichni s nimiž je sdílíme, dostanou stejný kontejner, který funguje stejným způsobem.
- **kontejnerizační platforma** - balí aplikace do izolovaných prostředí.

## Docker Images

- Images si můžeme představit jako recept, obsahuje všechny ingredience a instrukce.
- Docker Images Obsahují:
    - Všechny technologie které potřebujeme
    - Runtime
    - Nástroje a instrukce k tomu, aby náš kod běžel.

Nyní však potřebujeme něco co nám náš kod spustí..... **Docker Container**

## Docker Container

- Docker container je jako skutečné jídlo, které je uděláno z našeho předešlého receptu.
- Fascinující věcí je to, že pomocí jedné *Docker Image* jsme schopni udělat **několik** containerů.

### Cyklus Containeru

- **1. Vývoj** -> Vytvoření Dockerfile.
- **2. Build** -> Sestavení image z Dockerfile.
- **3. Distribuce** -> Nahrání image do registru. 
- **4. Deploy** -> Stažení a spuštění kontejneru.
- **5. Správa** -> Monitoring, updaty.