**Fetching a list of blocks**
```
|        | ----Request to/----> |        |
| Client | <------------------- | Server |
|  side  | ---Ajax to /block--> |  side  |
|        | <------------------- |        |
```
___

**Adding client-side javascript**

Place all fies under the public folder.
```
// index.html

<!DOCTYPE html>
<html lang='en'>
<head>
  <meta charset="utf-8">
  <title>Building Blocks</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Blocks</h1>
  <ul class='block-list'></ul>
</body>

<script src="jquery.js"></script> (1)
<script src="client.js"></script> (2)
</html>
```
- jquery to help manipulate the DOM and simply AJAX calls
- client.js is where custom client-side code that will talks to the express API
___

**Making AJAX calls**

Request to /blocks, then append results to block-list.
```
// client.js

$(function(){

// using jquery's get function, issue a request to /block endpoint
$.get('/blocks', appendToList);
// should return a list of block

// the return value of the ajax call is passed as an argument to the appendToList function
function appendToList(blocks){
  var list =[]; // create an empty array named 'list'
  for(var i in block){ // then it iterates through each blocks
    // create an LI html element for each one with a text set to block name
    list.push($('<li>', {test:block[i]}));
  }
  $('.block-list').append(list); // apeends list to the page
}
});
```
___

**Responding with JSON**

Create a new route for the /blocks endpoint.
```
// app.js

var express = require('express');
var app = express();

app.use(express.static('public'));

app.get('/block', function(req, res){
  var block = ['Fixed', 'Movable', 'Rotating']; // creating an array of blocks
  res.json(blocks); // serializing it back to the client using json function
});
```
