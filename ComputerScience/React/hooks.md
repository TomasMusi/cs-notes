# Hooks v Reactu

**Hooks** v Reactu jsou speciální funkce, které ti umožňují používat funkce Reactu  
(např. stav, životní cyklus, kontext…) uvnitř funkčních komponent.  
Dřív se tyto věci daly dělat jen v třídních komponentách, ale díky **hooks** už to jde jednoduše i ve funkcích.

---

## useState()

Účel **useState** je pracovat s reaktivními daty – tedy s daty, která se v aplikaci mění.  
Kdykoli se data změní, **useState()** přerenderuje UI.  
Stránka se tedy znovu vykreslí pokaždé, když se stav změní.

```js
// Count je reaktivní hodnota
// setCount je setter
const [count, SetCount] = useState(0)
```

Krátký příklad:

```TSX
<button onClick={() => setCount(count + 1)}>
 {count}
</button>
```


## useEffect()


Abychom pochopili **useEffect**, musíme nejdřív porozumět životnímu cyklu komponenty:

```TSX
componentDidMount(){
    // inicializováno – spustí se pouze jednou
}

componentDidUpdate(){
    // stav aktualizován
}

componentWillUnmount(){
    // komponenta zničena
}
```


```TSX
useEffect(() => {
    fetch('foo').then(() => setLoaded(true))
}, [])

// [] jsou dependencies – když je prázdné, efekt se spustí jen jednou, protože závislosti nejsou žádné.

/* Můžeme ho použít i se statem: */

useEffect(() => {
    fetch('foo').then(() => setLoaded(true))

    return () => alert('goodbye component!') // Spustí se před odstraněním komponenty z UI.
}, [count]) // Spustí se, když se změní count

```


## useContext()

Tento hook ti umožní pracovat s **React context API** – mechanismem,
který dovoluje sdílet data mezi komponentami bez nutnosti předávat **props**.

Představ si, že máme objekt **moods**, který může být „happy“ nebo „sad“.
Abychom sdíleli aktuální náladu mezi více oddělenými komponentami, vytvoříme **context**.
Jedna část aplikace může být „happy“ a jiná to automaticky převezme díky **Provider**.

```TSX

const moods = {
    happy: "",
    sad: ""
}

const MoodContext = createContext(moods);

function App(props){

    return (
        // Každý child uvnitř může zdědit hodnotu bez nutnosti předávat props
        <MoodContext.Provider value={moods.happy}>

        <MoodEmoji/>

        </MoodContext.Provider>

    )
}

function MoodEmoji(){
    // Když se nálada změní v parent provideru, hodnota se zde automaticky aktualizuje 
    const mood = useContext(MoodContext); // vezme hodnotu z nejbližšího parent provideru 


    return <p>{mood}</p>
}

```


## useRef() 

Tento hook umožňuje vytvořit **mutable objekt**, který si zachovává stejnou referenci mezi rendery.
Používá se, když chceš uchovat hodnotu, která se mění jako ve **state**,
ale rozdíl je v tom, že změna hodnoty v **useRef()** nevyvolá přerenderování UI.

```TSX

function App(){

    const count = useRef(0);

    return (
        // I když klikneme, hodnota se nezmění na UI!
        <button onClick={() => count.current++}> 
            {count.current}
        </button>
    );

}


/* Běžnější použití useRef() je pro získání nativních HTML elementů z JSX:  */

function App(){

    const myBtn = useRef(null);

    const clickIt = () => myBtn.current.click()

    return (

        <button ref={myBtn}></button>
    )

}

```

## useReducer()

## useMemo()
