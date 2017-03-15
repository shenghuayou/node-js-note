# node-js-note
 * basic node js
 * express js
 * mongoose js
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
  3. a simple mongo schema - From [Code For geek](https://codeforgeek.com/2015/08/restful-api-node-mongodb/)
```js
  var mongoose    =   require("mongoose");
  mongoose.connect('mongodb://localhost:27017/test');
  var mongoSchema =   mongoose.Schema;
  var userSchema  = {
      "userEmail" : String,
      "userPassword" : String
  };
  module.exports = mongoose.model('userLogin',userSchema);;

```
  4. Node.js and MongoDB Apps with Mongoose - From [scotch](https://scotch.io/tutorials/using-mongoosejs-in-node-js-and-mongodb-applications)
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

```js
  // if our user.js file is at app/models/user.js
  var User = require('./app/models/user');

  // create a new user called chris
  var chris = new User({
    name: 'Chris',
    username: 'sevilayha',
    password: 'password' 
  });

  // call the custom method. this will just add -dude to his name
  // user will now be Chris-dude
  chris.dudify(function(err, name) {
    if (err) throw err;

    console.log('Your new name is ' + name);
  });

  // call the built-in save method to save to the database
  chris.save(function(err) {
    if (err) throw err;

    console.log('User saved successfully!');
```
  5. to allow cross domain request in express
```js
  var express     =   require("express");
  var app         =   express();
  var allowCrossDomain = function(req, res, next) {
      res.header('Access-Control-Allow-Origin', "*");
      res.header('Access-Control-Allow-Methods', 'GET,PUT,POST,DELETE');
      res.header('Access-Control-Allow-Headers', 'Content-Type');
      next();
  }
  app.use(allowCrossDomain);
```
  
