## Exp Note 3

**Calling Node's HTTP function**
```
var express = require('express');
var app = express();

app.get('/', function(req, res){
// in call function
  res.write(''Hello World); // function passing in string
  // finish response  
  res.end();
  // both response are node function
});

app.listen(3000);
```

Run this code: $ curl http://localhost:3000
- will print out Hello World
