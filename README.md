# React-learning
This repo will help you to learn the ReactJS.

## How to install Bootstrap

```
    npm install --save bootstrap
```

```
Then add the following import statement to index.js file.

import '../node_modules/bootstrap/dist/css/bootstrap.min.css';

import '../node_modules/bootstrap/dist/js/bootstrap.min.js';

```

## Create data file

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
## Create Book Functional Component with event onClick

```

import React from "react";
import ReactDOM from "react-dom/client";

const Book = (props) => 
{
    const eventHandler = ()=>
    {
        alert('Testing Click event!!');
    };

    const showAuthor = (author)=>
    {
        alert(author);
    };

    const {BookName,AuthorName,BookDetail } = props.book;
    return ( 
        <div>
            <h1>{BookName}</h1>
            <h2>{AuthorName}</h2>
            <h3>{BookDetail}</h3>
            <button onClick={eventHandler}>Click Me</button> <span></span>
            <button onClick={()=>{alert(BookName);}}>Show Book Name</button> <span></span>
            <button onClick={()=>showAuthor(AuthorName)}>Show Author Name</button>
            <hr/>
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

## Bind and show data list

```
import logo from "./logo.svg";
import "./App.css";
import Book from "./Book";
import {books} from "./Books"

function App() {
  return (
    <div>
      {
        books.map(book=>{
        return (  
         <Book key={book.id}
            book = {book}>
          </Book>);

      })
    }
    </div>
  );
}

export default App;


```
