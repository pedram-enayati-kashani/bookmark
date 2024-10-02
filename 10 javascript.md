### DOM : document object model


**"use strict"** : It makes JavaScript check the code more strictly

##### function pure
```js
function sum(a,b){
    return a + b;
}
```

##### function impure
```js
let counter = 0;

function increment() {
  counter++;
  return counter;
}
```

##### Anonymous function
```js
return () => {
  console.log("Anonymous function");
}

```

### Array function

#### find
find make a loop and return one array value
```html
<p id="demo"></p>

<script>
const ages = [3, 10, 18, 20];

document.getElementById("demo").innerHTML = ages.find(checkAge);

function checkAge(age) {
  return age > 18;
}
</script>

output = 20
```

#### filter
let us filter array 

```html
<p id="demo"></p>

<script>
const ages = [32, 33, 16, 40];

document.getElementById("demo").innerHTML = ages.filter(checkAdult);

function checkAdult(age) {
  return age >= 18;
}
</script>
```

#### map
let us update value af array
```html
<p id="demo"></p>

<script>
const numbers = [65, 44, 12, 4];
const newArr = numbers.map(myFunction);

document.getElementById("demo").innerHTML = newArr;

function myFunction(num) {
  return num * 10;
}
</script>
```

#### Scop

**1.scope(block-function-global)**
```js
{
  let x = 3;
}
{
  const x = 4;
}
alert(x);

alert(carName);//err
function myFunc() 
{
  var carName = "Volvo";
  //code here can use carName
  // alert(carName);
}
alert(carName);//err

let x = 3;
var y = 9;
const PI = 3.14;

alert(PI);//true

function alertIt(){
  alert(PI);//true
}

xx();

alert(carName);

function xx()
{
  carName = "Toyota";//assignment
}

```

**2.hoisting**
```js
x = "sth";//assignment
var x;//declaration
var y = "sth else";//initialization



x = "some text";//assign
let elm = document.getElementById("demo");
elm.innerHTML = x;
var x;//declare


var x = "some text";//initialize
let elm = document.getElementById("demo");
elm.innerHTML = x + ' ' + y;//y=undefined
var y = "another text"//initialize
```


**3.strict mode("use strict")**
```js
x = 3.14;
alert(x);
myFunc();
alert(y)
function myFunc()
{
  "use strict";
  y = "some text";//assign
}
```

#### Javascript Class

**class**
```js
const demo = document.getElementById("demo");
class className{
    constructor(name,role){ /* when we add property javascript create a object with name property */
        this.name = name; /* assignment value property name to object name */
        this.role = role;
    }
    bio(){
        return "I am "+this.name+" a "+this.role + "<br>"
    }
    method2(x,y){alert(x+y);}
    method3(){}
    method4(){}
    method5(){}
}

let person1 = new className("Amir" , "programmer");
let person2 = new className("Mohammad" , "designer");
let person3 = new className("Sara" , "painter");

/*
demo.innerHTML = "I am "+person1.name+" a "+person1.role + "<br>";
demo.innerHTML += "I am "+person2.name+" a "+person2.role + "<br>";
demo.innerHTML += "I am "+person3.name+" a "+person3.role + "<br>";
*/
demo.innerHTML = person1.bio();
demo.innerHTML += person2.bio();
demo.innerHTML += person3.bio();

person1.method2(5,7);
```

**extends**

```js
const demo = document.getElementById("demo");
class className1{
    constructor(name,role){
        this.name = name;
        this.role = role;
    }
    bio(){
        return "I am "+this.name+" a "+this.role + "<br>"
    }
    method2(x,y){alert(x+y);}
    method3(){}
    method4(){}
    method5(){}
}
class className2{
    constructor(name,role,ex){
        this.name = name;
        this.role = role;
        this.ex = ex;
    }
    bio(){
        return "I am "+this.name+" a "+this.role + "<br>"
    }
}

class className3 extends className1{ /* when we extend of a class every method exist in that class , extended */
    constructor(name,year){ /* if you have same operation in constructor that you extend you don't need to write code again just use super */
        super(name);
        this.year = year;
    }
    bio2(){
        alert(this.bio());
    }
}


let person1 = new className1("Amir" , "programmer");
let person2 = new className1("Mohammad" , "designer");
let person3 = new className2("Sara" , "painter");
let person4 = new className3("Saeed" , 8);
alert(person4.bio2());

/*
demo.innerHTML = "I am "+person1.name+" a "+person1.role + "<br>";
demo.innerHTML += "I am "+person2.name+" a "+person2.role + "<br>";
demo.innerHTML += "I am "+person3.name+" a "+person3.role + "<br>";
*/
demo.innerHTML = person1.bio();
demo.innerHTML += person2.bio();
demo.innerHTML += person3.bio();

// person1.method2(5,7);

```