# Javascript

### variables

```js
// 3 ways to make variables
var hi = 'hello'
let hi = 'hello' // let is better
const hi = 'hello' // consts cant change
```

**variable types**
```js
// simple types
let hi = 'hello' // string
let num = 10 // number
let bool = true // boolean

// ARRAYS
let array = [1, 2, 3, "hi"] // square brackets = "array"
// access the items with square brackets
array[0] // 1
array[3] // "hi"

// arrays have some special functions:
// .map iterates through the array
array.map((item,index)=> console.log(item,index))
// .filter returns a NEW array filtered by the condition
const newArray = array.filter((item,index)=> item>2) // [3]
// .sort 
array.sort((a,b)=> a-b)
// push a new item into the array:
array.push(4) // [1, 2, 3, "hi", 4]

// OBJECTS
var o = {
    hi: 'hello',
    number: 22,
}
// access the items with dot notation
o.hi // hello
o.number // 22

// functions are also variables!
var funky = function(){
    console.log('a funky function')
}
```

### functions
```js
// function definition. It returns the answer (but not all functions need to return something)
// this function has 2 arguments, "a" and "b"
function add(a,b){
    // the body of the function
    return a+b
}
// calling a function (and passing in 2 values)
// now c = 3
var c = add(1,2)

// fat arrow syntax (mean "return")
// this is identical to the other one
// you dont have to type the word "function"!
var add2 = (a,b) => a+b 
```

### loops
```js
for(let i=0; i<100; i++) {
    console.log(i) // will print every number between 0 and 100
}

// .map !!! we use it in React all the time
[1,2,3].map((n,i)=> console.log(n,i))
```

### if statements
```js
if(3===2) {
    console.log('nope')
} else {
    console.log('yup')
}
if(3=='3') { // == only compares value
    console.log('YES!!')
}
if(3!=='3') { // === compares value AND type
    console.log('YES!!!')
}
if(true && false) { // and 
    console.log('nope')
}
if(true || false) { // or
    console.log('YESS!!!')
}

// "ternary expression" one-line if statement
var n = 2==='2' ? 10 : 'hello' // prints "hello"
```
```jsx
// ternary expressions are very useful in React code, to make dynamic props
<div style={{
    color: darkMode ? 'white' : 'black'
}} />

// or for dynamically rendering components
function Header(){
    const [settings, setSettings] = useState(false)
    return <div>
        { settingsToggled ? 
            <SettingsMenu /> :
            <ToggleButton />
        }
    </div>
}

// && is used a lot in React. In this example, SettingsMenu will only render if "settings" is true. (! means "not")
const [settings, setSettings] = useState(true)
return <div>
    {settings && <SettingsMenu />}
    {!settings && <ToggleButton />}
</div>
```