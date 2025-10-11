# Web Development rendering strategie.

Web development rendering strategie diktují kdy a kde se webpage HTML generuje, což ovlivňuje výkon, SEO a UX.

Než se můžeme kouknout na to, jaký způsob zvolit, musíme nejprve porozumět jak samostatný web funguje.

1. Krok - Build Process,  po napsání kodu potřebujeme buildnout náš kod skrze compiler, transpiler atd.

2. Krok - Nekdo zašle request URL na server, a náš Server udělá nějaký typ práce, skrze kterou zprocesuje stránku a request a zašle zpět stránku uživateli. 

## SSR - Server Side 

**Jak funguje?**
- Build time: Small
- Server: generuje celou HTML na každý request.
- Client: dělá minimální práci (hydration - propojí HTML k frontend frameworku.)

**Kdy to použít**
- Když pracujeme s dynamickými daty, user authentikací, SEO-kritické stránky.
- Často využíván s frameworky jako Next.js

**Výhody a Nevýhody**
- Výhody: Rychlejší načtení, lepší SEO, menší client workload.
- Nevýhody: Více server loadu než u static options.

## CSR - Client Side Rendering

**Jak funguje?**
- Build time: Small
- Server: zašle jenom blank HTML + Javascript soubory.
- Client: spustí Javascript k buildu a renderu celé stránky.
- Takto funguje jakákoliv React Aplikace pokud, neuděláš žádnou změnu.

**Kdy použít**

- Když nepotřebuuješ server k tomu, aby renderoval stránky.
- Dobrý pro rychlý setup a čistě client-based applikace.

**Výhody a Nevýhody**
- Výhody: Není potřeba backendu k tomu aby renderovalo stránku.
- Nevýhody: Heavy client workload,, pomalejší načítání, horší SEO. Práce na zařízení usera.

## SSG - Static Site Generation

**Jak funguje**
- Build time: dlouhý (pre-generates každou stránku jako static HTML) Když mám 1000 stránek tak to každou vygeneruje předem.
- Server: nedělá žádnou práci při requestu.
- Client: minimální práce.

**Kdy použít?**
- Pro static content: blog, dokumentace, stránky, kde se moc nemění data.

**Výhody/Nevýhody**
- Výhody: Velmi rychlý, minimální práce na straně serveru, Cache
- Nevýhody: Nevhodný pro dynamické nebo často měnící se data, dlouho trvá buildnout pro větší stránky.

## ISR - Incremental Static Regeneration

**Jak funguje?**
- Kombinace SSG + SSR
- Některé stránky prebuilt (SSG), ostatní build nebo rebuild na vyžádání (SSR)
- regenerování stránek, když data zastarají

**Kdy použít?**
- Velké weby s mnoha stránkami nebo semi-dynamic data.
- E-commerce sites, CMS-driven content

**Výhody a Nevýhody**
- Výhody: Rychlé jako SSG, podporuje dynamické updaty, kratší build time.
- Nevýhody: Větší složitost, mírně pomalejší u stránek regenerovaných na request.

