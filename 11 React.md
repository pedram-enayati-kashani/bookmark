### React

#### state
state is a object and save component dynamic data in system memory

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

**stateFull :** state full follow data and changed data
```js
class Main extends Component {
 constructor() {
   super()
   this.state = {
     books: []
   }
 }
 render() {
   <BooksList books={this.state.books} />
 }
}

or

class App extends Component {

    state = {
        count: 0,
        name: "Younes",
        family: "Ghorbany"
    }

    changeState() {
        this.setState({count: 5});
    }

    render() {
        let {count, name, family} = this.state;
        // count = 5;

        return (
            <div>
                <header>
                    <h1>شمارنده من</h1>
                </header>
                <p>{count}</p>
                <p>{name}</p>
                <p>{family}</p>

            </div>
        )
    }
}


```

**state less :** state less show data that send from props
```js
const BooksList = ({books}) => {
 return (
   <ul>
     {books.map(book => {
       return <li>book</li>
     })}
   </ul>
 )
}
```

#### bind
By default, the class method does not have access to this
```js

import {Component} from "react";

class Counter extends Component {

    constructor() {
        super();

        this.state = {
            name: "یونس"
        }

        // this.changeName = this.changeName.bind(this);
    }

    // changeName() {
    //     this.setState({name: "سجاد"})
    // }

    changeName = () => {
        this.setState({name: "سجاد"})
    }

    render() {
        return (
            <div>
                <p>{this.state.name}</p>
                <button onClick={this.changeName}>تغییر نام</button>
            </div>
        )
    }
}

export default Counter;
```

#### Style

```js

const myStyle = {color:'red',border:'1px solid red'};
// inline style

return (
    <div className="my-style"></div>

    or

    <div style={{color:'red',border:'1px solid red'}}></div>

    or

    <div style={myStyle}></div>
);

```

#### React Fragment
when we want return some element in a component we use React Fragment we use this because when we want create some element in react that's element must be in one parents element 

```jsx

<div>
    <h3>Contacts</h3>
</div>

or

<React.Fragment> /* we use this instead of div */
    <h3>Contacts</h3>
</React.Fragment>

/* for use */ 

import React from "react";

const Contacts = ()=>{
    return (
        <React.Fragment>
            <h3>Contacts</h3>
        </React.Fragment>
    );
}

or

import {Fragment} from "react";

const Contacts = ()=>{
    return (
        <Fragment>
            <h3>Contacts</h3>
        </Fragment>
    );
}

or

import {Fragment} from "react";

const Contacts = ()=>{
    return (
        <>
            <h3>Contacts</h3>
        </>
    );
}
```

#### Link
```jsx
import {Link} from "react-router-dom";

// with this you can create a link without refresh
<Link style={{ display: "block" }} to={`/books/${book.number}`} key={book.number}>
    {book.name}
</Link>
```

#### navLink
is exactly link link but you can add feature to link like active hover 
```jsx
    <NavLink
        style={({isActive}) => {
            return {
                display : "block",
                margin : "1rem 0",
                color: isActive ? "red" : "",
            }
        }}
        to={`/books/${book.number}${location.search}`}
        key={book.number}
    >
        {book.name}
    </NavLink>
```

#### Routes

```jsx
import {BrowserRouter,Routes,Route} from 'react-router-dom';

/* when we want use route must nest <Route> in <Routes> */
<Routes>
/* when we want nest a Route in another Route ... */
    <Route path="/" element={<App/>}> 
        <Route path="/about" element={<About/>}/>  
        <Route path="/books" element={<Books/>}>
            <Route index element={
                <main style={{padding:'1rem'}}>
                    <p>کتاب مورد نظر خود را قرار بدید</p>
                </main>
            }/>
            <Route path="/books/:bookId" element={<Book/>} />
        </Route>
        // this route is mean if url route didn't exist active button route  
        <Route path="*" element={
                <main style={{padding:"1rem"}}>
                    <p>گشتم نبود نگرد نیست</p>
                </main>
            } />
    </Route>
</Routes>
```

#### React life cycle
React life cycle include of
* Initialization component and given Props and default state
* render component
* update component
* destroy component

#### Hook
Hook is a funtion that let us use React life cycle in component without use class function

* **useSearchParams :** this exactly like state but Instead of save date in system memory it save date in url
* **useLocation :** give us info from url