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
   |                                  next();  // middleware A - calls nexts and middleware B responds back to the client
   |                                }); 
   |                                   ...
   |                                  next(); // middleware B - Calling next(); after response is complete will cause errors
   |                                   ...
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
