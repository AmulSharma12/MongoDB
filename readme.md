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

## 🚀 <b>MongoDB Installation  </b>

- Search MongoDB community server on google.
- [MongoDB community server link](https://www.mongodb.com/try/download/community) , Location might be change so search on google if not work.
- After installation copy both of the path and paste it in environement variables.
```path
C:\Program Files\MongoDB\Server\6.0\bin
C:\Program Files\MongoSH
```
- window+s  search EDIT THE SYSTEM ENVIRONMENT VARIABLES.
- click on environement variables -> inside user variables click on path -> edit option below -> new -> paste it ->okay
- use mongosh in cmd
```cmd
npm build
```
- Now you can good to go for query in mongosh shell.

## 🚀 <b>Cheatsheets of MongoDB query</b>

- showing all databases.
```
show dbs;
```
