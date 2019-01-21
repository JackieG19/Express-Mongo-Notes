## Installing and Writing Express

Installing Express
- $ npm install express @4.0 (install latest version from 4.9 branch)
- $ npm install express @3.15.2 (install specific version)

___
**Writing Hello World**
- calling the express function gives us an application instance
```
// app.js

var express = require('express');
var app = express(); // application intance
```
On the app object, call function that creates routes. The GET function creates a route that accepts HTTP GET request.
```
app.get('/', function(request, response){
// (root path, 
// callback function which will run each time the application receives a GET request
// (callback takes a request and a response object)) 

// will use the response object to send back the text() 
  response.send("hello world");
});

app.listen(3000); // binds application to TCP port 3000

```

The app.listen function takes an optional callback, which is called once the app is ready to start taking requests.
```
app.listen(3000, function(){
  console.log('Listening on port 3000');
});
// once server is up print to the console
```
