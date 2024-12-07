# Logbook2025
## A learning logbook for 2025


### 1/12/24

Yes - starting 2025 early!

https://www.youtube.com/watch?v=L0Pk3OVbxRU
Pro Vs Amateur Layouts (web design)

https://www.youtube.com/watch?v=DaeEKKSpgXU
$1,000,000 Design portfolios


# Review M.E.R.N stack development
# Mongo DB, Express, React, Node

Most of the backend is made - but this needs reviwing for understanding.

Next step is the React Front-End


###                                                             ---------------------------------------------------- 2/12/24 ---------------------------------------------------

#### MongoDB is a NoSQL database.  Rational databases are generally controlled with SQL (Structured Query Language) Popular ones include MySQL, SQL Server and PostgreSQL.

NoSQL databases in contrast are often called non-relational databases. They're a database not structured like a spreadsheet - i.e less rigid than an SQL databse.

The architecture of MongoDB is a NoSQL database which stores info in the form of collections and documents. MongoDB stores one or more collections. A collection represents
a single entity for example in an e-commerce app we need entities like categories, users, products etc. 
Each of these entities would be a single collection in the DB.

In MongoDB, a collection contains documents. A document is an instance of the entity containing the various 
relevant field values to represent the document.

E.G a product document will contain 'title', 'decription' and 'price' fields. 
Each field is a key-value pair e.g prce: 26, title: "Learning Node"

#### Express is a framework tha acts as a light layer atop of Node.js web server making it easier to develop Node.js applications.

It simplifies the API of Node.js, adds helpful features, helps organises our application's functionality with middleware and routing and many others.

#### CORS stands for Cross-Origin Resource Sharing
By default modern browsers don't allow frontend clients to talk to REST APIs - they will block requests sent from clients to the server as a secrity measure to make sure client-side browser javascript code can only talk to their own allowed server and not to some other servers that could potentially be malicious code.

To circumvent this we can enable CORS checking. The CORS package provides and Express middleware that can enable CORS.

#### The DOTENV dependency loads environmental variables from the process.env  file instead of setting environment variables on our development machne  which simplifies development.

******************************************************************
--------------------Do a back-end review--------------------------
******************************************************************

###                                                                ---------------------------------------------------- 3/12/24 ---------------------------------------------------

Back end review- 

Import express and cors middleware.
Create the server with;

const app = express()

Attach the middleware;

 app.use(cors())
 app.use(express.json())

express.json is the middleware to enable the server to read and accept JSON in a request.

the initial route is;

app.use("/api/v1/movies", movies)
app.use('*', (req,res) => {
 res.status(404).json({error: "not found"})
})

## Store the environment variables

This is stored int he .env file and a link in index.js to this file.

## Create our first route

import express from 'express';
const router = express.Router()
router.route('/').get((req, res) => res.send('hello world'))

export default router

## Creating Movies Data Access Object

This will allow our code to access movies in our database.

###                                                                ---------------------------------------------------- 4/12/24 ---------------------------------------------------

## Create the Movies Controller

Create the movies controller that the route file will use to access the doa file.

## Test the back end API
http://localhost:5000/api/v1/movies

A JSON return means it works :)

## Leaving Movie reviews

Using post, put and delete - post to create a new review, put for editing and delete for deleting.

Create the reviews.controller.js

## Test the reviews API

http://localhost:5000/api/v1/movies

Using one of the id - 

make a post request;

localhost:5000/api/v1/movies/review
provide a review body;

{
"movie_id": "573a1390f29313caabcd4135",
"review": "great movie",
"user_id": "1234",
"name": "john"
}

Test a put and a delete request.

### Create a route to Get a single movie and its ratings

In movies.route.js add two routes apiGetMovieById and apiGetRatings

******************************************************************
--------------------Back end review end--------------------------
******************************************************************

Next up - React Front End

###                                                                ---------------------------------------------------- 5/12/24 ---------------------------------------------------

### React

React uses re-usable components a bit like lego - these can be re-used without having to re-write code.

We will use React bootstrap to make the UI look more professional - it is a library of re-usable front end componentsthat contain JSX based templates
that help to build user interface components such as menus, sidebars, forms, buttons and icons etc.

React-router-DOM is also used to route different URLs to different parts of our web app.
The React-Router library interprets a browser URL as an instruction to navigate to various components.


### Create a nav bar

In the components folder we make four new components
-movies-list.js
-movie.js
-add-review.js
-login.js

###                                                                ---------------------------------------------------- 7/12/24 ---------------------------------------------------

Using a navbar component from bootstrap;

https://react-bootstrap.github.io/components/navbar/

import Nav from 'react-bootstrap/Nav'
import Navbar from 'react-bootstrap/Navbar'

function App() {
return (
<div className ="App">
 <Navbar bg="light" expand="lg">
  <Navbar.Brand href="#home">React-Bootstrap</Navbar.Brand>Navbar.Brand>
  <Navbar.Toggle aria-controls="basic-navbar-nav">
   <Navbar.Collapse id="basic-navbar-nav">
   <Nav className="mr-auto">
   <Nav.Link href="#home">Home</Nav.Link>Nav.Link>
   <Nav.Link href="#link">Link</Nav.Link>Nav.Link>
   </Nav>
   </Navbar.Collapse>
  </Navbar>
  </div>
  );
  }
