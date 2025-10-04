# Redis

Zkratka redis znamená: **RE**mote **DI**ctionary **S**erver: 

- Datové úložiště v paměti (in-memory) → data jsou držena v RAM pro extrémně rychlý přístup.

- Key-value databáze → něco jako velký slovník/hashmap.

- Podporuje komplexní datové struktury: řetězce, hashe, seznamy, množiny, seřazené množiny, streamy, bitmapy, hyperloglogy, geolokační indexy.

- Používá se často jako cache, databáze nebo message broker.

## Hlavní vlastnosti

- Caching → odlehčení hlavní databáze.
- Expirace dat → automatické mazání klíčů po určité době (TTL).
- Škálování → pokud máš víc serverů, všechny můžou sdílet stejné session v Redis (centrální cache).

## Kdy redis využít?

✅ Hodí se pro:

- Cache: zrychlení opakovaných dotazů (např. sessions, uživatelská data).
- Real-time analýzy: počítadla, žebříčky, trendy.

❌ Nevhodné pro:

- Primární databázi pro velké objemy dat (Redis je hlavně v RAM, ne na dlouhodobé uložení).
- Situace, kdy nemáš dostatek paměti RAM.
- Komplexní relační dotazy nebo JOINy (na to je SQL).


![RedisExplanation](pictures/redisExplanation.png)  
