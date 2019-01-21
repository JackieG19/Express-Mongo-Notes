## Exp-Note 4

**Responding with JSON**

The send function converts object and array to json:
```
app.get('/blocks', function(req, res){
  var blocks = ['Fixed', 'Movable', 'Rotating']; // an array with 3 element
  
  res.send(blocks);
  // to serialize this array to json is pass the array to the send function which will  
  // convert the array to json and set the proper response header automatically
});
```
Make request to the route:
- $ curl -i http://localhost:3000/blocks
- using -i to print the response header
```
HTTP/1.1 200 ok
X-Powered By: Express
Content-Type: application/json; charset = utf-8
(sets proper response headers was set to application/JSON)

['Fixed', 'Movable', 'Rotating']
response body in JSON format
```

___

**Responding with HTML**

The send function converts string to html
```
app.get('/blocks', function(req, res){
  var blocks = '<ul><li>Fixed</li><li>Movable</li><li>Rotating</li><ul>;
  res.send(blocks);
});
```
Responds with text/html
- $ curl -i http://localhost:3000/blocks
```
HTTP/1.1 200 ok
X-Powered By: Express
Content-Type: application/json; charset = utf-8

<ul><li>Fixed</li><li>Movable</li><li>Rotating</li><ul>
```
