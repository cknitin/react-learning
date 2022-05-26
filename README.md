# React Learning
This repo will help you to learn the ReactJS.

## Problem 1# How to install Bootstrap

```
    npm install --save bootstrap
```

#### Then add the following import statement to index.js file.

```

import '../node_modules/bootstrap/dist/css/bootstrap.min.css';

import '../node_modules/bootstrap/dist/js/bootstrap.min.js';

```
# Problem 2# How to bind list of books in ReactJS

## Create data file Books.js

```
export const books = [
    {
      id:1,
      AuthorName: "Amelia Hepworth",
      BookName: "I Love You to the Moon and Back",
      BookDetail: "Nice story book for children."
    },
    {
      id:2,
      AuthorName: "Eric Carle",
      BookName: "The Very Hungry Caterpillar",
      BookDetail: "Story of Hungry Caterpillar nice."
    },
     {
      id:3,
      AuthorName: "James Patterson",
      BookName: "Run, Rose, Run: A Novel",
      BookDetail: "Funny story of running Jack."
    }
  ];

```
## Create Book Functional Component with event onClick "Book.js"

```

import React from "react";
import ReactDOM from "react-dom/client";

const Book = props => {
  const eventHandler = () => {
    alert("Testing Click event!!");
  };

  const showAuthor = author => {
    alert(author);
  };

  const { BookName, AuthorName, BookDetail, ImgURL } = props.book;
  return (
    <div class="col-sm">
      <div className="card" style={{ width: 18 + "rem" }}>
        <img className="card-img-top" src={ImgURL} alt="Card image cap" />
        <div className="card-body">
          <h4 onClick={()=>{alert(BookName);}} className="card-title">{BookName}</h4>
          <h5 onClick={()=>showAuthor(AuthorName)} className="card-title">{AuthorName}</h5>
          <p className="card-text">{BookDetail}</p>
          <a onClick={eventHandler} href="#" className="btn btn-primary">
            Click Me
          </a>
        </div>
      </div>
    </div>
  );
};

// <div>
//     <h2>{props.bookName}</h2>;
//     <h3>{props.authorName}</h3>;
//     <h4>{props.bookDetail}</h4>;
// </div>

export default Book;


```

## Bind and show data list in App.js

```
import logo from "./logo.svg";
import "./App.css";
import Book from "./Book";
import {books} from "./Books"

function App() {
  return (
    <div class="container">
    <div class="row">
      {
        
        books.map(book=>{
        return (  
         
            <Book key={book.id}
                book = {book}>
            </Book>
         
          );
      })
    }
    </div>
    </div>
  );
}

export default App;

```

# Problem 3# React useState Hook

##  Import useState

```
import { useState } from "react";
```

## Initialize useState

```
const [count, setCount] = useState(0);
```

## Update State

```
const incrementCount = () => {
  setCount(count + 1);
};
```
## Example - Counter increment, decrement, rest

```
import React, { useState } from 'react';

const UseStateCounter = () => {
  const[value,setValue] = useState(0);

  const reset = ()=>{
    setValue(0);
  }

  return <div>
  <h3>{value}</h3>
  <button className="btn" onClick={()=>setValue(value-1)}>Decrement</button>
  <button className="btn" onClick={()=>setValue(value+1)}>Increment</button>
  <button className="btn" onClick={reset}>Reset</button>
  </div>;
};

export default UseStateCounter;


```

## Example - More complex counter using functional update

```
import React, { useState } from 'react';

const UseStateCounter = () => {
  const[value,setValue] = useState(0);

  const complexIncrement = ()=>{
    setTimeout(()=>{
      //setValue(value+1)
      setValue((prevState)=>{
          return prevState + 1;
      });
    },2000);
  }

  return <div>
  <h3>{value}</h3>
  <button className="btn" onClick={complexIncrement}>Complex Increment</button>
  </div>;
};

export default UseStateCounter;

```

## next, example Functional update

```
import React from 'react';
import { data } from '../../../data';
const UseStateArray = () => {
  const [people, setPeople] = React.useState(data);

  const removeItem = (id) => {
    
      setPeople((oldPeople)=>{
        let newPeople = oldPeople.filter((person) => person.id !== id);
        return newPeople;
      });
      
  };

  return (
    <div>
      {people.map((person) => {
        const { id, name } = person;
        return (
          <div key={id} className='item'>
            <h4>{name}</h4>
            <button onClick={() => removeItem(id)}>remove</button>
          </div>
        );
      })}
      <button className='btn' onClick={() => setPeople([])}>
        clear items
      </button>
    </div>
  );
};

export default UseStateArray;

```

## Show or Read State
```
<label>Show Count# {count}</label> <span></span> <span></span>
<button className="btn btn-info" onClick={incrementCount}>Increment</button>
```

## Create a single Hook that holds an object:
```
const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });
```

## Updating Objects and Arrays in State
```
const updateColor = () => {
    setCar(previousState => {
      return { ...previousState, color: "blue" }
    });
}
```
# Problem 4# Remove item and Clear all items in data
##Create a file "data.js", add data in it

```
export const data = [
  { id: 1, name: 'Harry Potter' },
  { id: 2, name: 'Hermione Granger' },
  { id: 3, name: 'Ron Weasley' },
  { id: 4, name: 'Draco Malfoy' },
  { id: 5, name: 'Luna Lovegood' }
];

```
## Crate a file "SetPeople.js"

```
import people from "./data"
import {useState} from "react"
import {data} from "./data"

function SetPeople()
{
    const[people,setPeople] = useState(data);

    const removeItem = (id)=>{
        let newPeople = people.filter((people)=>people.id !== id);
         setPeople(newPeople);
    }

    return (
        <div>
        {
            people.map(
                (people)=>{
                    const {id,name} = people;
                    return (<div key={id} className="item">
                            {people.name}
                            <button onClick={() => removeItem(id)}>remove</button>
                    </div>)
                }
            )
        }
            <button className="btn" onClick={()=>{ setPeople([]) }}>Clear All!</button>
        </div>
    );
}

export default SetPeople;
```

## Call the above file in App.js

```
import "./App.css";
import PeopleElement from "./SetPeople"

function App() {
  return (
    <div className="container">
      <PeopleElement/>
      
    </div>
  );
}

export default App;

```
# Problem 5# useState with object
## Update value in object

```
import React, { useState } from 'react';

const UseStateObject = () => {
  const[person,setPerson] = useState({
    name:"Peter",age:"21",message:"Good Morning"
  });

  const changeMessage = ()=>{
    setPerson({...person, message:"Good Night"});
  };

  return (
  <div>
    <h3>{person.name}</h3>
    <h3>{person.age}</h3>
    <h3>{person.message}</h3>
    <button className="btn" onClick={changeMessage}>Change Message</button>
  </div>);
};

export default UseStateObject;

```

# Problem 6# useState - Multiple state values
## Updating multiple states

```

import React, { useState } from 'react';

const UseStateObject = () => {
  
  const [name,setName] = useState('Harry')
  const [age,setAge] = useState(24)
  const [message,setMessage] = useState('Good Morning')


  const changeMessage = ()=>{
    setName("Rachel");
    setAge(21);
    setMessage("Good Night!!");
  };

  return (
  <div>
    <h3>{name}</h3>
    <h3>{age}</h3>
    <h3>{message}</h3>
    <button className="btn" onClick={changeMessage}>Change Message</button>
  </div>);
};

export default UseStateObject;

```
