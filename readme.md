## 🚀 <b>MongoDB</b>

- MongoDB is a document database designed for ease of development and scaling.
- MongoDB is a NoSQL database.
- As a javascript programmer, it looks like you are dealing with the javascript objects not with database.
- MongoDB includes :-
  - MongoDB Compass - It helps to deal with data in GUI.
  - MongoDB Atlas - database on the cloud.

## 🚀 <b>mongo vs mongod</b>

- mongo
  - mongo is command-line shell that connects to a specific instance of mongod.
  - you will issue the command to mongod to get the work done.
- mongod
  - mongod is the <b><i> Mongo Daemon</i></b> its basically the host process of the database.
  - mongod is actual process for managing data in database.
- conclusion : 2 process you must have to run
  - mongo - for command issue.
  - mongod - for taking action to that command.

## 🚀 <b>MongoDB vs MySQL </b>

- MySQL store data in form of table format whereas, MongoDB store data in json/bson format.
- MySQL and MongoDB database terms.
  - databases
  - tables = collections
  - rows = documents
  - columns = fields.
- MongoDB internally uses bson which is similar to json As, bson is more efficient than json.
- example of docuemnts and fields.
  - one document/row containing 4 fields with value.

```json
{
  "name": "xxx",
  "age": 10,
  "status": "A",
  "groups": ["news", "reports"]
}
```

## 🚀 <b>MongoDB Installation </b>

- Search MongoDB community server on google.
- [MongoDB community server link](https://www.mongodb.com/try/download/community) , Location might be change so search on google if not work.
- After installation copy both of the path and paste it in environement variables.

```path
C:\Program Files\MongoDB\Server\6.0\bin
C:\Program Files\MongoSH
```

- window+s search EDIT THE SYSTEM ENVIRONMENT VARIABLES.
- click on environement variables -> inside user variables click on path -> edit option below -> new -> paste it ->okay
- use mongosh in cmd

```cmd
npm build
```

- Now you can good to go for query in mongosh shell.

## 🚀 <b>Cheatsheets of MongoDB query in shell</b>

<br>

## 📌 <b>MongoDB - database related query syntax</b>

<br>

- Give all the databases.

```cmd
show dbs
```

- creating a new database
  - if database already exist switch to that database.

```sh
use databasename
```

- database you are currently working.

```sh
db
```

- Deleting the database
  - must check the database you are working by above command then only delete the database.

```sh
db.dropDatabase()
```

<br>

## 📌 <b>MongoDB - Collections/table related query syntax</b>

<br>

- creating new collection/table of users name

```sh
db.createCollections('users')
```

- droping the collection/table
  - users is the name of collection/table.

```sh
db.users.drop()
```

- <b><i>We will be working through out with users collection/table as an example.</i></b>

<br>

### 📌 <b>MongoDB - document/row related query syntax</b>

<br>

### ⭐ inserting document/row

- inserting a single document in a collections
  - it takes javascript object in form of key:value pair

```sh
db.users.insertOne({name:"xyz", age:21})
```

- insertMany() takes array of objects

```sh
db.users.insertMany(
  [
      {
          name:"amul"
          age:21
      },
      {
          name:"pedro",
          age:29
      }
  ]
)
```

### ⭐ Filter in collection/table using find()

- give all the rows/document in users table

```sh
db.users.find()
```
- give all the rows/document in pretty/formatted form
```sh
db.users.find().pretty()
```

- give all the rows/document in users table matching the object with name as amul.

```sh
db.users.find( {name:"amul"} )
```

### ⭐ updating document/row

- updating the existing document
  - update(filter , updation , options )
  - first object is filter, second updation, third option

```sh
db.users.update({name:'amul'},
  {
      $set:{
          name:'amul sharma'
      }
  }
)
```

### ⭐ deleting document/row

- deleting single document 
  - also if multiple document present  with that filter older document will be delete at first.

```sh
db.users.deleteOne({name:'amul'})
```

- deleting all the document with that filter

```sh
db.users.deleteMany({name:'amul'})
```

