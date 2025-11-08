cat > zaklady_goniometrie.md << 'EOF'
# Základy Goniometrie

V tomto dokumentu si probereme **sinus, kosinus a tangens**.  
Avšak nejprve je dobré znát, **kdy je vůbec můžeme využít a k čemu se hodí**.

---

## Kdy použít goniometrii

Pokud chceme pracovat se základy goniometrie, je očekávané, že již budeme znát **Pythagorovu větu**,  
která říká, že když máme **pravouhlý trojúhelník** (úhel 90°),  
dokážeme vypočítat jeho přeponu či odvěsnu, pokud známe dvě strany.

---

### Vzorce:

- **Pro přeponu:**

  $$ c = \sqrt{a^2 + b^2} $$

- **Pro odvěsnu:**

$$ b = \sqrt{c^2 - a^2} $$

*Přepona je vždy nejdelší strana trojúhelníku.*

---

## Když nemáme dvě strany

Často se stane, že **neznáme dvě strany**,  
ale máme **pravouhlý trojúhelník** a navíc **jeden úhel a jednu stranu**.

**A právě zde přicházejí goniometrické funkce!**

---

## Podobnost trojúhelníků

Když má trojúhelník stejné úhly, ale je větší nebo menší, **poměry jeho stran zůstávají stejné**.  
Takové trojúhelníky se nazývají **podobné trojúhelníky**.

Podobné trojúhelníky mají **stejné úhly** a **poměrně shodné (proporcionální) strany**.  
Strany jsou tedy **ve stejném poměru**.

---

### Příklad:

Trojúhelník má strany **3, 4, 5**  
a úhly **37°, 53°, 90°**  

Velký trojúhelník má stejné úhly (37°, 53°, 90°),  
ale strany třeba **6, 8, 10**.

Poměr:  
$$\frac{6}{3} = \frac{8}{4} = \frac{10}{5} = 2$$

Druhý trojúhelník je **dvakrát větší**, ale **tvar je stejný**.

---

## Proč fungují sin, cos a tan

Tohle je přesně důvod, **proč fungují sinus, kosinus a tangens!**  
Když máš úhel α, **poměr mezi stranami je vždy stejný**,  
ať je trojúhelník malý nebo obrovský.  

Proto sinus, kosinus a tangens **závisí jen na úhlu, ne na velikosti trojúhelníku**.

---

## Základní goniometrické funkce

| Funkce    | Vzorec                                                 | Co spojuje            | Použij, když znáš… | A chceš…                             |
| --------- | ------------------------------------------------------ | --------------------- | ------------------ | ------------------------------------ |
| **sin α** | $$\sin(α) = \frac{\text{protilehlá}}{\text{přepona}}$$  | protilehlou a přeponu | úhel + přeponu     | protilehlou                          |
| **cos α** | $$\cos(α) = \frac{\text{přilehlá}}{\text{přepona}}$$    | přilehlou a přeponu   | úhel + přeponu     | přilehlou                            |
| **tan α** | $$\tan(α) = \frac{\text{protilehlá}}{\text{přilehlá}}$$ | obě odvěsny           | úhel + přilehlou   | protilehlou *(nepotřebuješ přeponu)* |


---

![sin-cos-tan](../pictures/sin-cos-tan-showcase.png)


# Výpočet výšky stromu pomocí goniometrické funkce (tangens)

## Zadání:
Mám strom, u kterého chci zjistit, jak je vysoký.  
Když na něj svítí Slunce, jeho **stín měří 50 m** a  
**úhel dopadu slunečních paprsků je 30°**.

Chci zjistit výšku stromu (odvěsnu naproti úhlu).

---

## Co víme:
- úhel: α = 30°
- přilehlá strana (stín): b = 50 m
- hledaná strana: protilehlá (výška stromu) = a

---

## Použití tangensu:
$$
\tan(α) = \frac{\text{protilehlá}}{\text{přilehlá}}
$$

Dosadíme:
$$ \tan(30°) = \frac{a}{50} $$

$$
a = 50 \cdot \tan(30°)
$$

---

## Výpočet:
$$
\tan(30°) = \frac{1}{\sqrt{3}} \approx 0{,}577
$$

$$
a = 50 \cdot 0{,}577 = 28{,}9\,\text{m}
$$

---

## Výsledek:
> **Výška stromu je přibližně 28,9 metru.**

---

## Shrnutí:
| Známe | Hodnota |
|--------|----------|
| Úhel α | 30° |
| Přilehlá strana | 50 m |
| Tangens | 0,577 |
| Výška stromu | **≈ 28,9 m** |

---

**Použitý vztah:**  
$$\tan(α) = \frac{\text{protilehlá}}{\text{přilehlá}}$$



musíš používat něco takovyho: 
$$1 + 2 + 3 + \dots + n = \frac{n(n+1)}{2}$$

