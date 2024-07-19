### React

#### Imperative programming :
when you create tag , change tag , or set styled for tag in other you access to your document tags with dom

#### virtual dom
tree object type that send to react the real original map update dom and react According to map can update original dom


**point one :** the react check changed dom and According to that change update dom in other way react change dom from changed thing

**point two :** first change state next merge component and new state after that create virtual dom after comparing virtul dom and real dom, the changed things will be updated

**create project :**
```
create-react-app my-app
```

#### build
we use build when our project finished and we want send our project to host

---

#### component

**point one :** always name component start with uppercase word 

---

#### jsx
allow us to put html in javascript

**className :** in React Instead of using class, you should use className because the word class is reserved in JavaScript

**root element :** all element that you want create in component must be in a element root

**comment :** when you want create comment you must put your comment in ...
```js
{/* comment */} braise
```

**point one :** in jsx all of element must be closed
```html
<br/>
```

**import :** From version 17 onwards, there is no need to import react but if you import react it make a strict mode

---

#### function
```js
const MyApp = ()=>{
    return (
        <div className="MyApp">
            <h3>شمارنده من</h3>
            <br/>
            <Counter />
        </div>
    );
}
```

#### class
```js
class MyApp extends Component{
    render() { /* method class  */
        
    }
}
```

**point one :** if we want use constructor we must add super

```js
class Counter extends Component{
    
    constructor() {
        super();
    }
    
    render() {
        return (
            <div className="Counter">
                <p>شمارنده : {Math.floor(Math.random() * 1000)}</p>
                /* {} when ypu want mke int , "" when you want string */
            </div>
        );
    }
}
```

**different between class and functional:**
Previously, state was used only in class components, but now it can be used in functional components as well.

#### props
```js
  <Counter count={5}/>

  const Counter = (props)=>{
    return (
        <div className="Counter">
            <p>شمارنده : {props.count}</p>
        </div>
    );
}

or

class Counter extends Component{

    render() {
        const {count} = this.props.count
        return (
            <div className="Counter">
                <p>شمارنده : {count}</p>
            </div>
        );
    }
}

// Destructuring Objects

const Counter = ({count})=>{
    return (
        <div className="Counter">
            <p>شمارنده : {count}</p>
        </div>
    );
}
```

---

**function pure and impure in react :** in react render run just once and just props and change state make render run again 

**point two :** Props should never be changed or modified directly

**props children :** 
```js
  <Counter>
    what ever you write here send to render in object children
  </Counter>
```

**props default:** if props has not value it make show default value

```js
const Counter = ({count})=>{
    return (
        <div className="Counter">
            <p>شمارنده : {count}</p>
        </div>
    );
}

Counter.defaultProps = {
    count : 25,
}

or

const Counter = ({count})=>{
    return (
        <div className="Counter">
            <p>شمارنده : {count || 90}</p>
        </div>
    );
}
```

#### state
when we want add data , edit date , delete data in component we use state 