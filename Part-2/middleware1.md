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

**Executing Middleware functions**

When next is called, processing moves to the next middleware.
```
        (request comes in)
Client ---------> app.use(function(req, res, next){
   ^                 ...
   |                 next();  // middleware A
   |              }); // moves to the next middleware in the stack
   |              ...
   |                next(); // middleware B
   |              ...
   |                next(); // middleware C
   |                
   |------------- (completed request)
                 app.use(function(req, res, next){
                  ...
                  res.send('done'); // middleware N
                 });
```

A request comes in and it starts being processed in middleware A, which is added to the stack using the app.use function.

Middleware A function takes the requset and response objects as an argument, as well as the next function. 

The next function must be called in order to move proccessing to the next middleware in the sequence. 

Calling next from middleware A moves proccessing to middleware B. 

Calling next from B moves proccessing to C, and so on.

Keep doing this untill we reach a point where we want to respond back to the client, can be either from a route or middleware.
Call response.end from middleware N and complete the request.
___

**Returning from Middleware Functions**

The flow stops once the response is sent back to the client.
```
Client ----(request comes in)------ app.use(function(req, res, next){
   |                                  ...
   |                                  next();  // middleware A 
   |                                }); // - calls nexts and middleware B responds back to the client
   |                                   ...
   |                                  next(); // middleware B 
   |                                   ... // - Calling next(); after response is complete will cause errors
   |                                  next(); // middleware C
   |
   |
   |                  The flow stops once the response is sent back and any remaining 
   |                  middleware in the stack or user defined routes will not run.
   |
   |------(completed request)-----   app.use(function(req, res, next){
                                       ...
                                      res.send('done'); // middleware N
                                     });
```
