# Logbook2025
## A learning logbook for 2025


### 1/12/24

Yes - starting 2025 early!

https://www.youtube.com/watch?v=L0Pk3OVbxRU
Pro Vs Amateur Layouts (web design)

https://www.youtube.com/watch?v=DaeEKKSpgXU
$1,000,000 Design portfolios


Review M.E.R.N stack development
Mongo DB, Express, React, Node

Most of the backend is made - but this needs reviwing for understanding.

Next step is the React Front-End


### 2/12/24

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
