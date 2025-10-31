# Co je to gRPC API?

Než si vysvětlíme **gRPC**, musíme se krátce vrátit k **RPC** – *Remote Procedure Call*.

**RPC** je myšlenka, že místo posílání **raw data** přes síť může tvoje aplikace přímo volat funkci na jiném stroji, jako by byla lokální.

---

## Příklad

Například v kódu napíšeš `get user123` a na pozadí se tento **request** odešle přes síť, spustí se na serveru a vrátí výsledek.

```py
def run():
    channel = grpc.insecure_channel("localhost:50051")
    stub = user_pb2_grpc.UserServiceStub(channel)
    response = stub.GetUser(user_pb2.GetUserRequest(user_id=123))
    print(f"User: {response.id}, {response.name}, {response.age}")
```

Výsledek

```PY
User:123, Alice, 25
```

## Proč vzniklo gRPC

Původní systémy jako **XML-RPC** nebo **JSON-RPC** měly problémy – byly pomalé, textově náročné a neškálovaly dobře pro dnešní rozsáhlé realtime aplikace.  
A tady přichází **gRPC**.


---

## Co je gRPC

**gRPC** je moderní, vysoce výkonná verze **RPC** vytvořená Googlem.  
Představ si ho jako **Formuli 1 mezi API** – postavené pro rychlost, výkon a přesnost.

Zatímco **REST** posílá textový **JSON** přes **HTTP**,  
**gRPC** používá **Protocol Buffers (protobuf)**, které komprimují data do binárního formátu – extrémně rychlého na zpracování.

Je to jako rozdíl mezi posláním ručně psaného dopisu  
a zabalením všech souborů do ZIPu a jejich okamžitým odesláním.

**gRPC** také využívá **HTTP2**, což umožňuje posílat více **requests** současně přes jedno spojení.

---

## Komunikační vzory v gRPC

**gRPC** podporuje čtyři silné komunikační vzory:

1. **Simple request-response** – stejně jako **REST**  
2. **Server streaming** – pro živé aktualizace  
3. **Client streaming** – pro posílání kontinuálních dat  
4. **Bidirectional streaming** – obousměrná komunikace v reálném čase