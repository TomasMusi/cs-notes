# Co je to GraphQL

**GraphQL** znamená *Graph Query Language*.  
Byl vytvořen Facebookem a je to revoluční **query language**, který mění způsob, jakým získáváme data.

---

## Proč vznikl GraphQL

**GraphQL** řeší problém **over-fetching**, tedy získávání **příliš mnoho dat** – což je častý problém **REST API**.  

Potřebuješ jen jméno a e-mail uživatele?  
**REST** ti může poslat všechny jeho informace.  

**GraphQL** to celé obrací.  
Napíšeš jeden **query**, kde si přesně určíš, jaká data chceš – například jen username a email – a ostatní se přeskočí.  
Jeden **endpoint**, jeden **request**.

query {
    user(id: 123) {
        username,
        email
    }
}

---

## Reálný přínos GraphQL

Skutečná síla **GraphQL** je v **real-time subscriptions**.  
Tvoje aplikace může automaticky poslouchat živé aktualizace dat bez nutnosti opakovaných **requests**.