###### Date: 2023-11-2
MongoDB is a popular, open-source NoSQL database management system that falls into the category of document-oriented databases. It is designed to store and manage large amounts of data, especially unstructured or semi-structured data. MongoDB uses a flexible, schema-less data model, which makes it well-suited for a wide range of applications, including web applications, content management systems, mobile apps, and more.


### Mongodb with Express (Mongoose)
- Mongoose is an ODM (Object-Document Mapping) library for Node.js and MongoDB. It provides a way to interact with MongoDB databases using a more structured and schema-based approach than the native MongoDB driver. Mongoose simplifies the process of working with MongoDB by defining data models and schemas for your data, providing validation, query building, middleware hooks, and more.
- Install Mongoose by using following command :
```bash
npm i mongoose
```

- Lets create a db.js file where we can connect to the mongodb server and create schemas: 
```js
const mongoose = require("mongoose");
const dbConnect = mongoose.connect("mongodb://127.0.0.1:27017/practice");
if (dbConnect) {
console.log("DB connected sucessfully");
}
```

##### Schemas:
- In Mongoose, you define a schema for your data models, which describes the structure of your documents. A schema defines the fields, their data types, and any validation rules.
Lets create an schema for a model called users and schema for collections:
```js
const mongoose = require("mongoose");
const dbConnect = mongoose.connect("mongodb://127.0.0.1:27017/practice");
if (dbConnect) {
console.log("DB connected sucessfully");
}
const UserSchema = mongoose.Schema({
username: String,
name: String,
age: Number,
});
module.exports = mongoose.model("users", UserSchema);
```
This whole code will create an database called practice and collection called users and collection according to the given userschema!
 Now Lets Create an route in index.js file to push some data in the database: Folder Structure:[[Express🤓#Express Generator]]
 ```js
 //you must require the above file you exported on db.jh file!
 const userModel = require("./db");
 router.get("/user", async (req, res, next) => {
 const createduser = await userModel.create({
   username:"sandy",
   name:"Sandip",
   age:20
});
 res.send(createduser);
});
```

Here one user will created according to the above data provided ! You can check into your mongodb atlas !

- Finding all users/ fetching all data of an collection:
```js
router.get("/allusers", async (req, res, next) => {
let allUsers = await userModel.find();
res.send(allUsers);
});
```

- Fetching One Specific data from the collection:
```js 
router.get("/one", async (req, res, next) => {
let oneuser = await userModel.findOne({
username: "sandy",
});
res.send(oneuser);
});
```
यसले चहिँ collection बाट  username भन्ने ठाउँ बाट sandy search गारेर देखाउँछ।
- Deleting a data /user
```js
router.get("/delete", async (req, res, next) => {
let deletedUser = await userModel.findOneAndDelete({
username: "sandy",
});
res.send(deletedUser);
});
```
