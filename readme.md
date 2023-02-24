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

## 📌 <b>MongoDB - database related query syntax</b>
<hr>

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

## 📌 <b>MongoDB - Collections/table related query syntax</b>
<hr>

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

## 📌 <b>MongoDB - document/row related query syntax</b>
<hr>

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
  - also if multiple document present with that filter older document will be delete at first.

```sh
db.users.deleteOne({name:'amul'})
```

- deleting all the document with that filter

```sh
db.users.deleteMany({name:'amul'})
```

## 📌 <b>MongoDB - Operators</b>
<hr>

### ⭐ Compairison Operators

- $eq - return all document equal to specified value.

```sh
db.users.find( {age: {$eq:21}})
```

```sh
db.users.find( {name: {$eq:'amul'}})
```

- $lt - return all document less than specified value.

```sh
db.users.find( {age: {$lt:21}} )
```

- $lte - return all document less than equal to specified value.

```sh
db.users.find( {age: {$lte:21}} )
```

- $gt- return all document greater than specified value.

```sh
db.users.find( {age: {$gt:21}} )
```

- $gte- return all document greater than equal to specified value.

```sh
db.users.find( {age: {$gte:21}} )
```

- $gte- return all document not equal to specified value.

```sh
db.users.find( {age: {$ne:21}} )
```

### ⭐ Logical Operators

- $or- both condition should be true then it will return the document.
  - $and: [condition1 , condition2]

```sh
db.users.find(
  {
    $and: [
    {name: {$eq:'amul'}},
    {age: {$eq:21}}
    ]
  }
)
```

- $and - either of condition should be true it would return that document/row.
  - $or: [condition1 , condition2]

```sh
db.users.find(
  {
    $or: [
    {name: {$eq:'amul'}},
    {age: {$eq:29}}
    ]
  }
)
```

## 📌 <b>MongoDB - Indexing</b>
<hr>

### ⭐ Theory about Indexing

- we use indexing for optimizing the query.
- MongoDB internally use <i>B Tree Data Structure</i>
for implementing index. 
-  you should have good number of documents/rows to test the indexes.
- so using for loop just created more number of documents/rows in shell.
```sh
for(let i = 1; i<=4000; i++ )
{
  db.users.insertOne({ name:'user'+i , age:i })
}
```
- press enter now you have more number of documents
- <i> apply index in unique fields </i>

1. fire normal query 
```sh
db.users.find({name: 'user2000'}) 
```
2. you wont see difference that is totally ok but also see the time at which the query runs
```sh
db.users.find({name:'user2000'}).explain('executionStats')
```
- In executionStatus the value of 
  - executionTimeMillis is high
  - totalDocsExamined is no of documents.

- executionTimeMillis will be there with some value in milliseconds. But , in real time we dont have documents in thousand but in millions 

- Problem :- all the documents getting checked as well.
  - means even for one records it will check the whole
  thousand or millions of records which is time consuming.

- Solution:- using index we can solve this problem.
  - at name field we do indexing so the data get sorted and index will be maintained seprately that defines the data lies in which range.
  - now the document will not searched only index will searched will get document id and from there we will fetch the data. 


### ⭐ Creating indexes.

- createIndex() - it takes object and create index.
```sh
db.users.createIndex({ name:1 })
```
- Now run the same query after this command
```sh
db.users.find({name:'user2000'}).explain('executionStats')
```
- In executionStatus the value of 
  - executionTimeMillis dropdown
  - totalDocsExamined is also 1
- <i> So, wherever the data is in large scale and reading more time use index - amazon search bar</i>
- due to index - read becomes faster and write slower.
  - because you have to search in index and then update it .

### ⭐ Getting all the indexes in documents.

- getIndexes() - will give the array of objects.
```sh
db.users.getIndexes()
```
- Each object contains the name provided by MongoDB. 
- MongoDB provide bydefault index in _id field
  - if you are passing id for fetching the record fetch faster as well. 


### ⭐ deleting the index

- dropIndex() - it takes the name of the index and delete that index
```sh
db.users.dropIndex('name_1')
```
- Also check the _id will have index or not by executionStats
```sh
db.users.find({_id:ObjectId("63f8f4bcf5c6bda75cf2d664")}).explaind('executionStats')
```
- Less executionTimeMillis in milliseconds and totalKeysExamined is also 1 only means _id field is by default index provided by MongoDB. 