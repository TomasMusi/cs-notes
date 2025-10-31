# 🧠 Co je to REST API?

Představ si **REST API** jako číšníka v restauraci.  
Řekneš mu, co chceš, on jde do kuchyně, vezme to a přinese ti to zpět.  
Přesně to samé dělá REST API mezi tvojí **APP** a **serverem**.

---

## Co znamená REST?

**REST** = *Representational State Transfer*  
To jsou jen „chytře znějící“ slova pro jednoduchý způsob, jak spolu mohou aplikace komunikovat přes internet.

---

## HTTP methods

REST používá stejné **HTTP methods**, které už znáš z webu:

- **GET request** → slouží k získání dat, např. „ukaž mi všechny uživatele“  
- **POST request** → slouží k vytvoření nového záznamu, např. „přidej tohoto uživatele“  
- **PUT request** → slouží k aktualizaci existujících dat  
- **DELETE request** → slouží k odstranění dat

---

## Stateless

REST je **stateless**, což znamená, že každý **request** je zcela nezávislý.  
Server si **nepamatuje** tvoje předchozí **requests**, takže může obsluhovat miliony uživatelů bez zmatku.

---

## Platform independent

REST je **platform independent**.  
Tvoje **iPhone app**, **Android app**, **web app** nebo i **chytrá lednička** mohou všechny komunikovat se stejným **REST API**.
