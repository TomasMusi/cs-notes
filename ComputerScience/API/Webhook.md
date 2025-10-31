# Co je to WebHook API

Představ si, že u většiny API je tvoje aplikace jako člověk, který neustále kontroluje poštovní schránku.  
Vyjdeš ven, otevřeš ji, nic tam není, a zase se vrátíš – pořád dokola.  
Takto fungují tradiční API.

---

## Jak to WebHook mění

**WebHook** to celé obrací.  
Místo toho, aby ses ptal ty, **API volá tebe**.  
Je to jako pošťák, který zazvoní na zvonek přesně ve chvíli, kdy dorazí dopis.  
**Okamžité. Přímé. Efektivní.**

---

## Jak to funguje

Nastavíš si ve své aplikaci **callback URL**.  
Kdykoli nastane událost – například nová platba, odeslaný formulář nebo nový push kód –  
služba pošle **POST request** s detaily události přímo na tvůj **callback URL**.  

Žádné opakované dotazy, žádné zbytečné **requests**.  
Jen **real-time** aktualizace.

---

## Proč se WebHooky nazývají „reverse APIs“

**WebHooky** se často popisují jako **reverse APIs**.  
Místo aby tvoje aplikace honila data, **data přicházejí k ní**.

---

## Příklady z praxe

- **GitHub** spouští **WebHook**, když je nahrán nový kód.  
- **Shopify** ho aktivuje, když je vytvořena nová objednávka.
