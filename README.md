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
