columnhelper.accessor
columnhelper.display
columnhelper.group
 
getRowModel
getVisibleCells
getContext
createColumnHelper
flexRender()

# TanStack Table

## createColumnHelper<User>()

Toto vytváří pomocný objekt, který zná strukturu tvých dat (**User**),  
takže všechno, co následně definuješ (sloupce, accesory atd.), se řídí tímto typem.

---

### columnHelper.accessor()

Vytváří **data column** – sloupec, který automaticky čte konkrétní vlastnost z datových řádků.

```TS
        const columns = [
            columnHelper.accessor("name", {
                header: "Name",
                cell: info => info.getValue(),
            }),
        ]

        // "name" znamená row.name — přistupuje ke klíči z každého datového řádku.
        /*
        Toto je užitečné, když chceš automaticky řešit věci jako třídění, filtrování a seskupování.
        */
``` 

### columnHelper.display() 
    
Vytváří **non-data** sloupec – tedy takový, který neodpovídá žádné vlastnosti v datech.

```TS 
        const columns = [
            columnhelper.display({
                id: "actions",
                header: "Actions",
                cell: () => <button>Delete</button>
            }),
        ];

        // Ideální pro Buttons(Edit/Delete), Checkboxes, Serial numbers / row numbers, Custom Layouts.
        // Používá se, když sloupec přímo neodpovídá objektu s daty.
```

### columnHelper.group() 

Používá se ke **skupinování více sloupců** pod jeden nadřazený header.

```TS
        const columns = [
            columnHelper.group({
                header: "User info",
                columns: [
                    columnHelper.accessor("name", { header: "Name" }),
                    columnHelper.accessor("email", { header: "Email" })
                ]
            })
        ]

        // Vytvoří tabulku, kde "User Info" je nadpis, který spojuje dva sloupce pod sebou.
        /*
        Používá se pro vícestupňové záhlaví – např. v dashboardech nebo reportech.
        */
```

### getRowModel() 

Funkce, která říká tabulce, **jak vypočítat řádky** – z dat po všech transformacích (filtrování, třídění, stránkování atd.).

```TS
    const table = useReactTable({
        data, 
        columns,
        getCoreRowModel: getCoreRowModel(),
    });
    /* Později můžeš nahradit např. getFilteredRowModel(), getSortedRowModel() atd. */
```

### getVisibleCells()

Vrací **buňky, které jsou aktuálně viditelné** v daném řádku – po aplikaci viditelnosti, seskupování nebo skrytí sloupců.

```TSX
    {row.getVisibleCells().map(cell) => (
        <td key={cell.id}>
        {flexRender(cell.column.columnDef.cell, cell.getContext())}
        </td>
    )}
```

### getContext()

Každý header nebo cell má svůj **context objekt**,
který obsahuje vše potřebné – data řádku, informace o sloupci, stav tabulky atd.

```TS
    flexRender(header.column.columnDef.header, header.getContext())

    /*
    Kdykoli použiješ flexRender k vykreslení headeru nebo cellu, potřebuje context.
    Zajišťuje, že renderovací funkce dostanou správné hodnoty a metadata.
    Bez contextu by TanStack nevěděl, kterou buňku nebo řádek vykresluješ.
    */
```

### flexRender()

Univerzální renderer pro jakýkoli obsah ve sloupci nebo buňce –
ať už je to string, React komponenta nebo funkce.

```TS
    {flexRender(cell.column.columnDef.cell, cell.getContext())}

    /* Pokud byl tvůj cell definován takto: */

    cell: (info) => <strong>{info.getValue()}</strong>
    // Pak flexRender tuto funkci správně vykoná.
```

