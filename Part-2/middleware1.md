**Mounting Middleware**

The app use function adds middleware to the application stack.
```
// app.js

var express = require('express');
var app = express();

// to use middleware must call the static function in the express object:
app.use(express.static('public'));

// pass it to the root folder where we want to serve our static file from the return value of that
// function call is passed to the app.use function, this is all to do to server static files from
// the public folder

app.listen(3000); // the static middleware defaults to serving the index file
```
___

**Understanding Middleware**

Functions executed sequentially that access request and response.
```
|~~~~~~~~| ------------> | middleware - A  = Validation
| Client |               | middleware - B  = Authentication
|________| <------------ | middleware - C  = Data Parsing
              
              app.get('/block' ...)
```

Middleware and Express are functions added to the stack that have access to the request 
and response objects and are executed sequentially. Inside of each middleware we can do 
things: Validation, Authentication, and Data Parsing. So when a request comes in, it
passes through each middleware before reaching our routes.
