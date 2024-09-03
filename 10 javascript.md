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