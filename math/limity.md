# Limita

## Co je to limita

Limita funkce je takové „co se děje, když se $x$ **blíží** k nějakému číslu“.
Nezajímá nás nutně přesně hodnota v tom bodě, ale **kam funkce míří**.

Mám funkci

$$
f(x) = 2x
$$

Chci limitu, když $x \to 3$.

To znamená: „Co se stane s $f(x)$, když se $x$ blíží k 3?“

- Když dosadíš $x = 2.9$, dostaneš $f(2.9) = 5.8$.
- Když dosadíš $x = 2.99$, dostaneš $f(2.99) = 5.98$.
- Když dosadíš $x = 3.01$, dostaneš $f(3.01) = 6.02$.

👉 Vidíš, že to leze k **6**.

Takže:

$$
\lim_{x \to 3} 2x = 6
$$


### Příklad

Chci limitu, když $x \to 2$:

$$
\lim_{x \to 2} \frac{x^2 - 4}{x - 2}
$$

### 1. Přímé dosazení
Dosadím $x=2$:

$$
\frac{2^2 - 4}{2 - 2} = \frac{4 - 4}{0} = \frac{0}{0}
$$

Dostávám $\frac{0}{0}$ → **undefined** (nevíme jakou hodnotu reprezentuje).  
Musíme tedy výraz upravit.

---

### 2. Úprava výrazu
Rozložíme čitatel:

$$
x^2 - 4 = (x - 2)(x + 2)
$$

Dosadíme do zlomku:

$$
\frac{x^2 - 4}{x - 2} = \frac{(x-2)(x+2)}{x-2}
$$

Pro $x \neq 2$ se $(x-2)$ pokrátí:

$$
= x + 2
$$

---

### 3. Výpočet limity
Teď už můžeme spočítat limitu:

$$
\lim_{x \to 2} (x+2) = 2 + 2 = 4
$$

---

### 4. Kontrola dosazením "blízko 2"
- Když $x = 1.9$, dostanu $\frac{1.9^2 - 4}{1.9 - 2} = \frac{3.61 - 4}{-0.1} = \frac{-0.39}{-0.1} = 3.9$
- Když $x = 2.1$, dostanu $\frac{2.1^2 - 4}{2.1 - 2} = \frac{4.41 - 4}{0.1} = \frac{0.41}{0.1} = 4.1$

👉 Vidíš, že to **leze k hodnotě 4**.

---

✅ Výsledek:

$$
\lim_{x \to 2} \frac{x^2 - 4}{x - 2} = 4
$$


### Příklad

Chci limitu, když $x \to 3$:

$$
\lim_{x \to 3} \frac{x^3 - 27}{x - 3}
$$

### 1) Přímé dosazení
$$\frac{3^3-27}{3-3}=\frac{27-27}{0}=\frac{0}{0}$$  
→ **nedefinováno** ⇒ výraz musíme upravit.

---

### 2) Rozklad pomocí rozdílu třetích mocnin

**Pozor, správný vzorec je:**

$$\boxed{a^3 - b^3 = (a-b)\cdot(a^2+ab+b^2)}$$

Použijeme jej pro $a = x,\; b = 3$:

$$
x^3-27=(x-3)(x^2+3x+9)
$$

Dosadíme do zlomku a pokrátíme $(x-3)$ (platí pro $x \neq 3$):

$$
\frac{x^3-27}{x-3}=\frac{(x-3)(x^2+3x+9)}{x-3}=x^2+3x+9
$$

---

### 3) Výpočet limity
$$\lim_{x \to 3}(x^2+3x+9)=3^2+3\cdot3+9=9+9+9=27$$

---

✅ **Výsledek:**
$$\boxed{\lim_{x \to 3} \frac{x^3 - 27}{x - 3} = 27}$$


### Příklad

Chci limitu, když $x \to 3$:

$$\lim_{x \to 3} \frac{\tfrac{1}{x} - \tfrac{1}{3}}{x - 3}$$

---

### 1) Přímé dosazení
$$\frac{\tfrac{1}{3} - \tfrac{1}{3}}{3 - 3} = \frac{0}{0}$$  
→ **nedefinováno**, musíme upravit.

---

### 2) Úprava čitatele – společný jmenovatel
V čitateli je rozdíl zlomků, dáme je na společný jmenovatel:

$$\frac{1}{x} - \frac{1}{3} = \frac{3 - x}{3x}$$

---

### 3) Úprava celého výrazu
Dosadíme zpět:

$$\frac{\tfrac{1}{x} - \tfrac{1}{3}}{x - 3}
= \frac{\tfrac{3 - x}{3x}}{x - 3}
= \frac{3 - x}{3x \cdot (x - 3)}$$

A teď využijeme, že $3 - x = -(x - 3)$:

$$\frac{3 - x}{3x \cdot (x - 3)} = \frac{-(x - 3)}{3x \cdot (x - 3)} = -\frac{1}{3x}$$  

(pro $x \neq 3$)

---

### 4) Výpočet limity
$$\lim_{x \to 3} -\frac{1}{3x} = -\frac{1}{3 \cdot 3} = -\frac{1}{9}$$

---

✅ **Výsledek:**
$$\boxed{\lim_{x \to 3} \frac{\tfrac{1}{x} - \tfrac{1}{3}}{x - 3} = -\tfrac{1}{9}}$$


### Příklad

Chci limitu, když $x \to 9$:

$$\lim_{x \to 9} \frac{\sqrt{x} - 3}{x - 9}$$

---

### 1) Přímé dosazení
$$\frac{\sqrt{9} - 3}{9 - 9} = \frac{3 - 3}{0} = \frac{0}{0}$$  
→ **nedefinováno**, musíme upravit.

---

### 2) Úprava pomocí *racionalizace* (násobení konjugovaným výrazem)

Pravidlo:  

\[(\sqrt{a} - \sqrt{b})(\sqrt{a} + \sqrt{b}) = a - b\]

Vynásobíme čitatel i jmenovatel výrazem $(\sqrt{x} + 3)$:

$$\frac{\sqrt{x} - 3}{x - 9} \cdot \frac{\sqrt{x} + 3}{\sqrt{x} + 3}
= \frac{(\sqrt{x} - 3)(\sqrt{x} + 3)}{(x - 9)(\sqrt{x} + 3)}$$

---

### 3) Uplatníme vzorec $a^2 - b^2$
$$(\sqrt{x} - 3)(\sqrt{x} + 3) = x - 9$$

Tedy:

$$\frac{(\sqrt{x} - 3)(\sqrt{x} + 3)}{(x - 9)(\sqrt{x} + 3)}
= \frac{x - 9}{(x - 9)(\sqrt{x} + 3)}$$

Pro $x \neq 9$ se $(x - 9)$ pokrátí:

$$= \frac{1}{\sqrt{x} + 3}$$

---

### 4) Výpočet limity
Teď už můžeme dosadit přímo:

$$\lim_{x \to 9} \frac{1}{\sqrt{x} + 3} = \frac{1}{\sqrt{9} + 3} = \frac{1}{3 + 3} = \frac{1}{6}$$

---

✅ **Výsledek:**
$$\boxed{\lim_{x \to 9} \frac{\sqrt{x} - 3}{x - 9} = \tfrac{1}{6}}$$


## Limita a Graf