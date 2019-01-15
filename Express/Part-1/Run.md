## Exp Note 2

**Running Express app**

- $ node app.js (node command filename)
- in the terminal: listening on port 3000
- $ curl http://localhost:3000/ (a request to local host 3000)
- return response - Hello world
- Whenever code is changed in application
  - must restart the process / require a server restart, 
  - in the command line use control(ctrl) c to stop the server, interrupting the current process.
  
**The Request and Response objects**
  
Express extends node http object
  
  app.js
  ```
  app.get('/', function(req, res){
    ...
  });
  ```
  
  lib/request.js
  ```
  var req = exports = module.export = {
    --proto--:http.IncomingMessage.prototype
    
    // --proto-- inheritance look like javascript
    // prototype - objects from node HTTP
  };
  ...
  ```
  The request object inherits from Incoming Message
  
  lib/response.js
  ```
  var res = module.exports = {
    --proto--:http.ServerResponse.prototype
  };
  ...
  ```
 The response object inherits from Server Response
  
