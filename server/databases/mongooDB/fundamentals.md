### MongoDB-Mongoose-Express-Node.js

![mongoDB-diagram](images/mongoDB.png?raw=true "MongoDB Express/Node.js Diagram") </br>
The diagram above shows the interaction between the different stacks. 

### Storing info
![mongoDB-storeinfo](images/mongoDB-storeinfo.png?raw=true "MongoDB store info diagram") </br>
Mongo stores record in different collections. Every collection can have many different records. Every records is a JSON object.  Collections are schemaless; inside of every collection records with different properties can be included. 

### Mongoose
Mongoose is an Object Document Mapper (ODM). This means that Mongoose allows you to define objects with a strongly-typed schema that is mapped to a MongoDB document. Mongoose provides functionality around creating and working with schemas. 
![mongoose-functionality](images/mongoose.png?raw=true "Mongoose functionality") </br>

### Define types
SchemaTypes handle definition of path defaults, validation, getters, setters, field selection defaults for queries, and other general characteristics for Strings and Numbers. The following are all the valid SchemaTypes in mongoose.
- String
- Number
- Date
- Buffer
- Boolean
- Mixed
- ObjectId
- Array
- Decimal128
- Map

```js
const mongoose = require('mongoose');

const { Schema } = mongoose;

const userSchema = new Schema({
  googleId: String,
  credit: Number
});

mongoose.model('users', userSchema);
```


### Subdocuments
Subdocuments are documents embedded in other documents. In Mongoose, this means you can nest schemas in other schemas. Mongoose has two distinct notions of subdocuments: arrays of subdocuments and single nested subdocuments.</br>

![mongoDB-subdocument](images/mongoDB-subdocument.png?raw=true "MongoDB Subdocuments") </br>

Subdocuments are similar to normal documents. Nested schemas can have middleware, custom validation logic, virtuals, and any other feature top-level schemas can use. The major difference is that subdocuments are not saved individually, they are saved whenever their top-level parent document is saved.


