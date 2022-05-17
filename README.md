# React-learning
This repo will help you to learn the ReactJS.

## How to install Bootstrap

```
    npm install --save bootstrap
```

#### Then add the following import statement to index.js file.

```

import '../node_modules/bootstrap/dist/css/bootstrap.min.css';

import '../node_modules/bootstrap/dist/js/bootstrap.min.js';

```

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
