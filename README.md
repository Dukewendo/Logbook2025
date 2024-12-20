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


Bootstrap has different components that you can use - simply go tot he documentation and copy the markup then update it for your own purposes.                                                               

Bootstrap has different components that you can use - simply go tot he documentation and copy the markup then update it for your own purposes.

Make the change;

**<Link to={"/movies"}>Movies</Link>**

and

**{ user ? (**
**<a>Logout User</a>**
**) : (**
**<Link to={"/login"}>Login</Link>**
**)}**

###                                                                ---------------------------------------------------- 8/12/24 ---------------------------------------------------

Above is known as conditional rendering.

We can use a react hook like so;

function App() {
const [user, setUser] = React.useState(null)

async function login(user = null) {//default user to null
setUser(user)
}

async function logout() {
setUser(null)
}

The hook lets us add some local state to functional components.

### Defining routes

<Switch>
<Route extract path={["/", "/movies"]} component={MoviesList}>
</Route>
 <Route path="/movies/:id/review" render={(props)=>
  <AddReview  {...props} user={user} />
   }>
  </Route>

  <Route path="/movies/:id/" render={(props)=>
  <Movie  {...props} user={user} />
   }>
  </Route>

   <Route path="/login" render={(props)=>
  <Login  {...props} login={login} />
   }>
  </Route>

</Switch>

We use a Switch component to switch between different routes. The Switch component renders the first toute that matches.


###                                                                ---------------------------------------------------- 9/12/24 ---------------------------------------------------

Catch up on MongoMovies React Frontend.
Clearing up install of React, adding basic pages to be worked on at a later date.
Update install and set routes for pages.

Setting state for log in / log out using the hook React.useState - set to null initially for no user and set to null on logout.

Cleaned up and updated routing code and learned <a> tages cannot be inside Nav.Link components as under the 
hood Nav.Link in bootstrap is an ,a> tage and they cannot be nested together- using <button> instead of <a>
as this is better for accessibility.

``` <Router>
			<div className="App">
				<Navbar bg="light" expand="lg">
					<Navbar.Brand href="#home">Movie Reviews</Navbar.Brand>
					<Navbar.Toggle aria-controls="basic-navbar-nav" />
					<Navbar.Collapse id="basic-navbar-nav">
						<Nav className="mr-auto">
							<Nav.Link as={Link} to={"/movies"}>
								Movies
							</Nav.Link>
						</Nav>
					</Navbar.Collapse>
				</Navbar>
				{user ? (
					<Nav.Link as="button" onClick={logout}>
						Logout User
					</Nav.Link>
				) : (
					<Nav.Link as={Link} to="/login">
						Login
					</Nav.Link>
				)}
				<Routes>
					<Route path="/" element={<MoviesList />} />
					<Route
						path="/movies/:id/review"
						element={<AddReview user={user} />}
					/>
					<Route path="/movies/:id/" element={<Movie user={user} />} />
					<Route path="/login" element={<Login login={login} />} />
				</Routes>
			</div>
	</Router>
```
Up next - 
### Connecting front to back!

We will create a service class. A service is a class with a well-defined specific function. In our case, our service is responsible for taking to the backend to get and save data.
Service classes provide their functionality to be consumed by components.

###                                                                ---------------------------------------------------- 10/12/24 ---------------------------------------------------



Not has a lot of time this evening- working late then fixing a new oven!

Create a service to connect fron to back in mongomovies.

###                                                                ---------------------------------------------------- 11/12/24 ---------------------------------------------------

#### https://axios-http.com/docs/intro

A promise based HTTP clien for node.js.
It is isomorphic - on browser OR node.js

Features:


    Make XMLHttpRequests from the browser
    Make http requests from node.js
    Supports the Promise API
    Intercept request and response
    Transform request and response data
    Cancel requests
    Timeouts
    Query parameters serialization with support for nested entries
    Automatic request body serialization to:
        JSON (application/json)
        Multipart / FormData (multipart/form-data)
        URL encoded form (application/x-www-form-urlencoded)
    Posting HTML forms as JSON
    Automatic JSON data handling in response
    Progress capturing for browsers and node.js with extra info (speed rate, remaining time)
    Setting bandwidth limits for node.js
    Compatible with spec-compliant FormData and Blob (including node.js)
    Client side support for protecting against XSRF

Why use Axios?

Axios helps developers make HTTP requests from NodeJS or XMLHttpRequests from a browser. If the request is successful, you will receive a response with the data requested.
If the request fails, you will get an error. You can also intercept the requests and responses and transform or modify them.

```
import axios from "axios";

class MovieDataService {
	getAll(page = 0) {
		return axios.get(`http://localhost:5000/api/v1/movies?page=${page}`);
	}

	get(id) {
		return axios.get(`http://localhost:5000/api/v1/movies/id/${id}`);
	}

	find(query, by = "title", page = 0) {
		return axios.get(
			`http://localhost:5000/api/v1/movies?${by}=${query}&page=${page}`
		);
	}

	createReview(data) {
		return axios.post("http://localhost:5000/api/v1/movies/review", data);
	}
	updateReview(data) {
		return axios.put("http://localhost:5000/api/v1/movies/review", data);
	}
	deleteReview(id, userId) {
		return axios.delete("http://localhost:5000/api/v1/movies/review", {
			data: { review_id: id, user_id: userId },
		});
	}
	getRatings() {
		return axios.get("http://localhost:5000/api/v1/movies/ratings");
	}
}

export default new MovieDataService();
```
getAll returns all movies.
get(id) returns a specific movie with an id.
find() is the same endPoint as getAll except it has query which consists of user-entered search.
createReview, updateReview, deleteReview and getRatings are self-explanitory.

###                                                               ---------------------------------------------------- 12/12/24 ---------------------------------------------------

Implimenting MoviesList component to consume the functionality in MovieDataService.
Components are meant to be responsible for rendering view supported by application logic for better UX.

Added useState hook for movies, searchTitle, searchRating and ratings.

The useEffect hook is called after rendering. An empty array is provided [] as we only want useEffect to be called once when the component first renders.


Next - creating a search form...... tomorrow!

###                                                               ---------------------------------------------------- 13/12/24 ---------------------------------------------------

onChangeSearchTitle will be called whenever a user types into the search title field.
onChangeSearchTitle will then take the entered value and set it to the component state.

Getting late - more tomrrow!

###                                                             ---------------------------------------------------- 14/12/24 ---------------------------------------------------

```Importing bootstrap components for the form as so;
import Form from "react-bootstrap/Form";
import Button from "react-bootstrap/Button";
import Col from "react-bootstrap/Col";
import Row from "react-bootstrap/Row";
import Container from "react-bootstrap/Container";
```

Making a simple react search formwith a seach by title field and a search by ratings.

Tomorrow we display movies using cards.

###                                                             ---------------------------------------------------- 15/12/24 ---------------------------------------------------

Adding front end for card using bootstrap components;

```
import Card from "react-bootstrap/Card";
return (
	<div className="App">
		<Container>
			<Form>
				<Row>
					<Col>
						<Form.Group>
							<Form.Control
								type="text"
								placeholder="Search by title"
								value="{searchTitle}
						onChange={onChangeSearchTitle}"
							></Form.Control>
						</Form.Group>
						<Button variant="primary" type="button" onClick={findByTitle}>
							Search
						</Button>
					</Col>
					<Col>
						<Form.Group>
							<Form.Control as="select" onChange={onChangeSearchRating}>
								{" "}
								{rating.map((rating) => {
									return <option value={rating}> {rating}</option>;
								})}
							</Form.Control>
						</Form.Group>
						<Button variant="primary" type="button" onClick={findByRating}>
							Search
						</Button>
					</Col>
				</Row>
			</Form>
			<Row>
				{movies.map((movie) => {
					return (
						<Col>
							<Card style={{ width: "18rem" }}>
								<Card.Img src={movie.poster + "/100px180"} />
								<Card.Body>
									<Card.title>{movie.title}</Card.title>
									<Card.Text>Rating: {movie.rated}</Card.Text>
									<Link to={"/movies/" + movie._id}> View Reviews </Link>
								</Card.Body>
							</Card>
						</Col>
					);
				})}
			</Row>
		</Container>
	</div>
);

```
###                                                             ---------------------------------------------------- 16/12/24 ---------------------------------------------------

Not doing much tonight but watched bootstrap video here;

https://www.youtube.com/watch?v=8pKjULHzs0s


###                                                             ---------------------------------------------------- 17/12/24 ---------------------------------------------------

Implimenting findByTitle and findByRating functions.

###                                                             ---------------------------------------------------- 18/12/24 ---------------------------------------------------

No much time tonight so reviewing front end so far.

###                                                             ---------------------------------------------------- 19/12/24 ---------------------------------------------------

App testing...

###                                                             ---------------------------------------------------- 20/12/24 ---------------------------------------------------

More bug fixing;

```
[eslint] 
src/components/movies-list.js
  Line 19:1:    React Hook "useEffect" cannot be called at the top level. React Hooks must be called in a React function component or a custom React Hook function  react-hooks/rules-of-hooks
```
and

```
[eslint] 
src/components/movies-list.js
  Line 37:17:   'resonse' is not defined      no-undef
  Line 73:9:    'searchRaing' is not defined  no-undef
  Line 97:12:   'rating' is not defined       no-undef
  Line 130:16:  'App' is not defined          no-undef
```

late night codeing after work - i need to be checking spellings!

Tomorrow -Bugfix the search component.
