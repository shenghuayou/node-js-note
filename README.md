# node-js-note
 * basic node js
 * express js
 * mongoose js
 * passport js
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
  6. A simple example for how to use passport js in handling login and signup - From [Agraj Mangal](https://code.tutsplus.com/tutorials/authenticating-nodejs-applications-with-passport--cms-21619)
```js
  // passport/login.js
  passport.use('login', new LocalStrategy({
      passReqToCallback : true
    },
    function(req, username, password, done) { 
      // check in mongo if a user with username exists or not
      User.findOne({ 'username' :  username }, 
        function(err, user) {
          // In case of any error, return using the done method
          if (err)
            return done(err);
          // Username does not exist, log error & redirect back
          if (!user){
            console.log('User Not Found with username '+username);
            return done(null, false, 
                  req.flash('message', 'User Not found.'));                 
          }
          // User exists but wrong password, log the error 
          if (!isValidPassword(user, password)){
            console.log('Invalid Password');
            return done(null, false, 
                req.flash('message', 'Invalid Password'));
          }
          // User and password both match, return user from 
          // done method which will be treated like success
          return done(null, user);
        }
      );
  }));
```
  7. mongoose promise basic codes - From [eddywashere](http://eddywashere.com/blog/switching-out-callbacks-with-promises-in-mongoose/)
```js
  var promise = User.findById('123').exec();

  promise.then(function(user) {
    user.name = 'Robert Paulson';

    return user.save(); // returns a promise
  })
  .then(function(user) {
    console.log('updated user: ' + user.name);
    // do something with updated user
  })
  .catch(function(err){
    // just need one of these
    console.log('error:', err);
  });
```
  8. To have socket.io and express js running in the same port.
```js
  var express = require('express')
  var app = express()
  var server = require('http').createServer(app)
  var io = io.listen(server)

  server.listen(80);
```
  9. Create simple chat application using Node.JS, Express.JS and Socket.IO
    - http://javabeginnerstutorial.com/javascript-2/create-simple-chat-application-using-node-js-express-js-socket-io/
