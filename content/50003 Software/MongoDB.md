# MongoDB
---
## School lessons
using mongo shell:
- Dont use shell helper commands like `show dbs` inside the shell script

During the writing of nodejs code for mongo db, there are alot of keywords that follow this $
- examples: $exists,
- Used in the find function


**Lecture 108** (Overview: What is MongoDB?)
- A NoSQL Database which stores "Documents" in "Collections" (as opposed to "Records" in "Tables" in SQL)
- Used to store application data
- Enforces no data schema or relations
- Easily connected to node.express, not to react

**Lecture 109** (Difference between SQL and NOSQL)
| NoSQL                                                                              | SQL                                    |
| ---------------------------------------------------------------------------------- | -------------------------------------- |
| Enforces no data schema                                                            | Enforce a strict Data Schema           |
| less focused on relations                                                          | Relations are a core feature           |
| works with independent documents                                                   | Records are Related                    |
| Great for: Logs, ORders, MEssages, fast for high frequency of incoming information | Pros: shopping carts contacts networks |
**Lecture 110** (Do not connect frontend (React) to database (Server))

**Lecture 111** (Setting up MongoDB)
Use MongoDB Atlas
Setup Cluster
Whitelist personal IP address
Create new user for database access

**Lecture 112** (connecting DB to simple backend)
create a js file called mongo.js
	- create a createProduct and getProducts function to be exported
install mongo db
connect to cluster by copying a connection string from online into mongo.js

**Lecture 113** (creating a new document)
instantiate some constants before creating stuff
do it in the try catch block
close connection after document is added

**Lecture 114** (getting data/document from database)
need to create a try catch block to retreive data
do it asynchronously via `await client.connect()`
find method returns cursor
Can get array via `find().toArray()`
need to close the client after try catch block
However, this is a very long and clunky code
Use mongoose as a helper to make things easier

**Lecture 115** (installing mongoose)
note that mongoose is better for databases with schemas

**Lecture 116** (Creating schemas)
can send in json data into schema when defining a schema

**Lecture 117** (Creating a product)
Create a js file that has a a function for creating a product

**Lecture 118** (Connecting database and saving the product/entry into database)
use mongoose.connect() method to connect to mongodb database and also have .then() and .catch() methods to log details to console. all this is done inside the mongoose file

**Lecture 119** (Getting products)
find is a static method that can be used on the Product. There is a mongoose version of find
.cursor() turns it back into a cursor

**Lecture 120** (Understanding the ObjectID)
they are an ObjectID data type
needs to be converted into a string which mongoose has a convenient method to do so 
using `.id`

**Lecture 121** (Wrap Up)
using mongodb driver is cumbersome, USE MONGOOSE
Mongoose gives us schema and blueprints which makes things easier

**Lecture 123** (Module Introduction)
Integrating Mongoose & MongoDB into the places project
Creating the right schema and model for places project

**Lecture 124** (Recap of installing mongoose and connecting project to database. Link to 112)
Nothing new

**Lecture 125** (Creating Place schema and model)

**Lecture 126** (How to save created place/document into Mongoose? Link to 113)
Remember that saving is a asynchronous task

**Lecture 127** (Getting places via placeID)
Place.findById() does not return a real promise;
It takes in an Id as a parameter
place.toObject()

**Lecture 128** (Getting places via UserID (another attribute))
Round 2 of Lecture 127
note that **find** is an async operation, so function needs to be declared as async and itself needs to be declareed with await

**Lecture 129** (Update Places)
use getplacebyId again
set getters = true? same thing repeated in previous video

**Lecture 130** (Delete Places)
repeat the get and then later delete an entry
not very difficult or new

**Lecture 131** (Adding users to the app)
step 1: creating user logic
step 2: establish relationship between user and places later

**Lecture 132** (Creating User model)
Can use unique keyword in the scheme to make querying faster
By using mongoose unique validator for validating if email/field already exists in database. Needs unique attribute to be set to true

**Lecture 133** (using the user model for signup)
edit the existing signup code in users-controllers

**Lecture 134** (Adding the user login)
Not the final validation
but utilises the mongodb 

**Lecture 135** (Get all the users functionality)
concept of protection: '-password' to remove the user pw details when find() return user data

**Lecture 136** (Adding Relation between places & users)
In the places Schema, change data type of creator to a User model.

**Lecture 137** (Creating places and adding it to a user only; only create transaction if id exists)
pre-creation code at 1 min mark
Do checks before adding places to a user
undo all operations if either operations fails
- need to have transactions and sessions
- start a session first
- then init transaction is successful
- session finishes
- transactions are then committed

**Lecture 138** (Deleting place and removing it from user)
Only if the connection is existing, then we are allowed to use populate method
- 'creator' argument is used

**Lecture 139** (How to getplaces by user id using populate method)
hmm?

**Lecture 140** (Cleaning up code)
remove dummy arrays

**Lecture 141** (Wrap Up)
create schemas
create users and places in controllers using schemas
use `ref` to link place and user together

#webp