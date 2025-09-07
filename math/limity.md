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

Chci limitu, když $x \to 3$:

$$
\lim_{x \to 3} \frac{x^3 - 27}{x - 3}
$$

### 1) Přímé dosazení
$$
\frac{3^3-27}{3-3}=\frac{27-27}{0}=\frac{0}{0}
$$
→ **nedefinováno** ⇒ výraz upravíme.

---

### 2) Rozklad pomocí rozdílu třetích mocnin

**Pozor, správný vzorec je zvýrazněně:**

\[
\boxed{\;a^3-b^3=(a-b)\,(a^2+ab+b^2)\;}
\]

Použijeme jej pro \(a=x,\; b=3\):

$$
x^3-27=(x-3)\,(x^2+3x+9)
$$

Dosadíme do zlomku a pokrátíme \((x-3)\) (platí pro \(x\neq3\)):

$$
\frac{x^3-27}{x-3}=\frac{(x-3)(x^2+3x+9)}{x-3}=x^2+3x+9
$$

---

### 3) Výpočet limity
$$
\lim_{x\to3}(x^2+3x+9)=3^2+3\cdot3+9=9+9+9=27
$$

---

✅ **Výsledek:**
$$
\boxed{\;\displaystyle \lim_{x \to 3} \frac{x^3 - 27}{x - 3}=27\;}
$$
