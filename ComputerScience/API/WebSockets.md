# Co jsou to WebSockets

**WebSockets** jsou jako otevření trvalé telefonní linky mezi tvojí aplikací a serverem.  
Jakmile je spojení navázáno, obě strany spolu mohou kdykoli okamžitě komunikovat.

---

## Žádné čekání

Už žádné čekání na to, až klient pošle dotaz jako u tradičního **HTTP**.  
Komunikace probíhá v reálném čase, obousměrně a bez přerušení.

---

## Jak to funguje

Začíná to tzv. **handshake**.  
Tvůj prohlížeč pošle speciální **HTTP request** s žádostí: „Pojďme to povýšit na WebSocket Connection“.  
Server souhlasí, „podají si ruce“ – a od té chvíle zůstává kanál otevřený.  
Tím vznikne trvalé obousměrné komunikační spojení.

---

## Výhody WebSockets

**WebSockets** umožňují serveru okamžitě poslat data ve chvíli, kdy se něco stane.  
Jsou také velmi flexibilní – můžeš posílat **plain text**, **JSON** pro strukturovaná data,  
nebo dokonce **binární soubory**, jako jsou obrázky a videa.
