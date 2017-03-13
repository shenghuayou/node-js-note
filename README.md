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
