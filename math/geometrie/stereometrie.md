# 🔷 Co je to stereometrie?

- **Stereometrie** je část geometrie, která se zabývá **tělesy v prostoru (3D útvary).**

- Na rozdíl od **planimetrie** (tam řešíš trojúhelníky, čtverce, kruhy v rovině) se tady díváš na **krychle, koule, jehlany, válce…**

- V matematice tě zajímá **jejich tvar, objem, povrch a vzájemné vztahy v prostoru.**

## 🔷 Co se v ní počítá?

1. **Vzájemná poloha** – zda se body, přímky a roviny protínají, jsou rovnoběžné, mimoběžné.
1. **Vzdálenosti a úhly v prostoru** – např. úhel mezi přímkami, vzdálenost bodu od roviny.
1. **Síť tělesa** – když těleso „rozstřihneš“ a rozložíš na rovinu (např. krychle → 6 čtverců).
1. **Povrch tělesa** – součet obsahů všech jeho stěn.
1. **Objem tělesa** – kolik „prostorové hmoty“ těleso vyplňuje.
1. **Složená tělesa** – např. válec + kužel dohromady, nebo koule vložená do krychle.


| Těleso | Povrch S | Objem V | Vysvětlení |
|---|---|---|---|
| **Krychle** (hrana $a$) | $S=6a^2$ | $V=a^3$ | Krychle má 6 stejných čtverců → plocha jednoho čtverce $a^2$, krát 6. Objem = délka × šířka × výška, ale všechny hrany jsou stejné, proto $a\cdot a\cdot a$. |
| **Kvád­r** (hrany $a,b,c$) | $S=2(ab+bc+ac)$ | $V=a\cdot b\cdot c$ | Má 6 stěn: 2 obdélníky $ab$, 2 obdélníky $bc$, 2 obdélníky $ac$. Objem = délka × šířka × výška. |
| **Hranol** (podstava plocha $P$, obvod podstavy $o$, výška $v$) | $S=2P+o\cdot v$ | $V=P\cdot v$ | Hranol = „válec, ale místo kruhu je jiný tvar“. Povrch = dvě podstavy $2P$ + plášť (obvod podstavy × výška). Objem = plocha podstavy × výška. |
| **Jehlan** (podstava plocha $P$, výška $v$) | $S=P+S_{boční}$ | $V=\tfrac13 P\cdot v$ | Povrch = podstava + součet obsahů trojúhelníkových stěn (záleží na tvaru podstavy). Objem = třetina objemu hranolu se stejnou podstavou a výškou. |
| **Válec** (poloměr $r$, výška $v$) | $S=2\pi r^2 + 2\pi r v$ | $V=\pi r^2 v$ | Povrch = dvě kruhové podstavy $(2\pi r^2)$ + plášť (obvod kruhu $2\pi r$ × výška $v$). Objem = plocha podstavy $(\pi r^2)$ × výška. |
| **Kužel** (poloměr $r$, výška $v$, strana $s=\sqrt{r^2+v^2}$) | $S=\pi r^2 + \pi r s$ | $V=\tfrac13 \pi r^2 v$ | Povrch = podstava (kruh $\pi r^2$) + plášť (obloukový trojúhelník, tj. $\pi r s$). Objem = třetina objemu válce se stejnými rozměry. |
| **Koule** (poloměr $r$) | $S=4\pi r^2$ | $V=\tfrac{4}{3}\pi r^3$ | Povrch = čtyřikrát plocha kruhu poloměru $r$. Objem = „nafouknutý kruh“ – čtyři třetiny objemu koule poloměru $r$. |

### Jak chápat symboly

- **$a, b, c$** – délky hran (používá se u kvádru, krychle).

- **$P$** – plocha podstavy (to, na čem těleso „stojí“).

    - Čtverec: $P=a^2$

    - Obdélník: $P=a \cdot b$

    - Kruh: $P=\pi r^2$

- **$o$** – obvod podstavy.

    - Čtverec: $o=4a$

    - Obdélník: $o=2(a+b)$

    - Kruh: $o=2\pi r$

- **$v$** – výška (vzdálenost mezi podstavami nebo od podstavy k vrcholu).

- **$r$** – poloměr (u kruhu nebo koule).

- **$s$** – šikmá strana kužele (počítá se podle Pythagora: $s=\sqrt{r^2+v^2}$).

### Příklad, abys to viděl

Měj kvádr s hranami:

- $a = 2 ,\text{cm}$

- $b = 3 ,\text{cm}$

- $c = 5 ,\text{cm}$ 

**Povrch**

Vzorec:

$$
S = 2(ab + bc + ac)
$$

Dosazení:

$$
S = 2(2 \cdot 3 + 3 \cdot 5 + 2 \cdot 5) = 2(6 + 15 + 10) = 62 \,\text{cm}^2
$$

**Objem**

$$
V = a \cdot b \cdot c
$$

Dosazení:

$$
V = 2 \cdot 3 \cdot 5 = 30 \,\text{cm}^3
$$

**📐 Povrch tělesa (označuje se $S$)**

- Povrch je **součet všech ploch**, které tvoří vnější „obal“ tělesa.
- Jako kdybys to těleso chtěl obalit papírem → potřebuješ znát, kolik papíru spotřebuješ.
- Měří se ve **čtverečních jednotkách** (např. cm², m²).

**Příklad**

- Krychle o hraně $a=2$ cm.
- Každá stěna je čtverec o obsahu $a^2 = 4$ cm².
- Má 6 stěn, takže povrch je $6 \cdot 4 = 24$ cm².

**📦 Objem tělesa (označuje se $V$)**

- Objem udává, **kolik místa těleso zabírá uvnitř**.
- Jako kdybys to těleso chtěl naplnit vodou → objem říká, kolik vody se tam vejde.
- **Měří se v krychlových jednotkách** (např. cm³, m³).

**Příklad:**

- Stejná krychle o hraně $a=2$ cm.
- Objem se počítá $a^3 = 2^3 = 8$ cm³.
- To znamená, že se do krychle vejde 8 malých krychliček o hraně 1 cm.