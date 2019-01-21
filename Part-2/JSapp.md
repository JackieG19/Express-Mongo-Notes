**Rich javascript application**

They allow for a more interactive experience on the web.
```
|        | ----- 1. Intitial request --------> |        |
| Client | <----- 2. index.html is returned -- | Server |
|        | ----- 3. Ajax requests -----------> |        |
|        | <----- 4. JSON is returned -------- |        |


1. The browser issues the initial request to the server 

2. The server responds with HTML

3. Further requests are issued through javascript and ajax

4. The server responds with data, typically JSON and 
   the client uses that to update elements on the page
```
___

**Writing index.html**

Place html file under the public folder.
```
// index.html

<!DOCTYPE>
<html>
<head>
  <meta charset="UTF-8">
  <title>Building Blocks</title>
</head>
  <body>
    <h1>Blocks</h1>
  </body>
</html>
```
___

**Serving files with sendFile**

The index.html file is served from Express
```
// app.js

var express = require('express');
var app = express();

//create a get route for the root path:
app.get('/', function(req, res){
  
  // from the callback
  response.sendFile(__dirname + '/public/index.html');
 // this function takes the path of the file we want  to server, use the __dirname,
 // which returns the current path of the application, then append /public/index.html,
 // which cause the html file to be served back to the client.
});

app.listen(3000); // listen to port 3000
```



