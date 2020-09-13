# react!

### making components
```js
// a Person component that shows person's name
function Person(props){
  return <div style={{fontSize: props.age}}>
    {props.name}
  </div>
}
```

### use a component
```js
// here, you render the Person component
// and pass in the name "alice" in a prop
<Person name="alice" age={30} />
```

### looping over components using .map()
```js
function App(){
  const people=['Alice','Bob','Casey','Diana']
  return <div>
    {people.map((item,index)=> {
      // "key" is something that React needs
      return <Person key={index} name={item} />
    })}
  </div>
}
```

### useState
```js
// "state" lets you handle changes on your site
// in an intelligent way
function Counter(){
  const [count,setCount] = useState(0)
  return <button onClick={()=> setCount(count+1)}>
    You clicked me {count} times!
  </button>
}
```

### conditionally rendering components
```js
// you can use && to render a component based on some javascript condition
function App(){
  return <div>
    {1+1===2 && <WillRender />}
    {1+1===3 && <WontRender />}
  </div>
}
// you can also use "ternary expression" to conditionally render a component
function App(){
  return <div>
    {1+1===2 ? <WillRender /> : <WontRender />}
  </div>
}
```

### useEffect
```js
function App(){
  useEffect(()=>{
    // run some code once on startup
  }, [])
  return <div>hello world</div>
}
```

**or use useEffect more dynamically**
```js
function Person(props){
  useEffect(()=>{
    // this code will run EVERY time
    // that the persons "age" changes
  }, [props.age])
  return <div>{props.age}</div>
}
```


### useRef
```js
// auto focus an input!
function App(){
  const divRef = useRef()
  useEffect(()=>{
    divRef.current.focus()
  }, [])
  return <input ref={divRef}
    placeholder="hello world"
  />
}
```


### example app
```js
import React, {useState, useEffect} from 'react';
import './App.css';

const counterz=[{
  label:'Add One', n:1, initial:5
},{
  label:'Minus Two', n:-2
},{
  label:'Add 100', n:100
}]

function App() {
  return (
    <div className="App">
      {counterz.map((c,i)=>{
        return <Counter key={i} // React needs a "key"
          label={c.label} n={c.n} initial={c.initial}
        />
      })}
    </div>
  )
}

function Counter(props){
  const {label, n, initial} = props
  const [count, setCount] = useState(initial||0)
  return <div style={{marginTop:25}}>
    <button onClick={()=> setCount(count+n)}>
      {label}
    </button>
    <div>
      {count}
    </div>
  </div>
}

export default App;

```



### animations with React
```js
function TextInput({show}){
  const [width] = useState(Math.random()*300)
  const inputRef = useRef()
  useEffect(()=>{
    if(show) {
      setTimeout(()=> inputRef.current.focus(), 250)
    }
    else inputRef.current.blur()
  }, [show])
  return <input ref={inputRef} 
    placeholder="hello world"
    style={{
      width: width,
      transition: 'all 0.2s',
      transform: show ? 
        'translate(0,0) rotate(0)' : 
        'translate(400px,0) rotate(180deg)',
      opacity: show ? 1 : 0,
    }}
  />
}
```
