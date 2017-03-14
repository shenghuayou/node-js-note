# node-js-note
 * basic node js
 * express js
 * example codes

## Example ##
  1. basic code for setup express.
  ```js
    var express = require('express')
    var app = express()

    app.get('/', function (req, res) {
      res.send('Hello World')
    })

    app.listen(3000)
  ```
  
  2. axios get and post method example. - From [CodeHeaven](http://codeheaven.io/how-to-use-axios-as-your-http-client/)
  ```js
    // Performing a GET request
  axios.get('https://api.github.com/users/' + username)
    .then(function(response){
      console.log(response.data); // ex.: { user: 'Your User'}
      console.log(response.status); // ex.: 200
    });  

  // Performing a POST request
  axios.post('/save', { firstName: 'Marlon', lastName: 'Bernardes' })
    .then(function(response){
      console.log('saved successfully')
    });  
  ```
  
  3. Node.js and MongoDB Apps with Mongoose - From [scotch](https://scotch.io/tutorials/using-mongoosejs-in-node-js-and-mongodb-applications)
```js
  // grab the things we need
  var mongoose = require('mongoose');
  var Schema = mongoose.Schema;

  // create a schema
  var userSchema = new Schema({
    name: String,
    username: { type: String, required: true, unique: true },
    password: { type: String, required: true },
    admin: Boolean,
    location: String,
    meta: {
      age: Number,
      website: String
    },
    created_at: Date,
    updated_at: Date
  });

  // the schema is useless so far
  // we need to create a model using it
  var User = mongoose.model('User', userSchema);

  // make this available to our users in our Node applications
  module.exports = User;
```
  
  
