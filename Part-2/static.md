**Reading the static middleware source**

The code for static is a good example of express middleware.
```
// index.js

exports = module.exports = function serverStatic(root, option){
  ...

  return function serverStatic(req, res, next){
  // static only cares about GET/HEAD requests
  
    if(req.method !== 'GET' && req.method !== 'HEAD');
    // for any other type of request, static call next
    return next()
    
    // immediately passes processing to whatever is next on the stack, otherwise it
    // does its work and a send stream pipes its content to the response object.
    ...
    stream.pipe(res)
  }
}
```
___

**Serving static assets**

The static middleware serves everything under the specific folder(/public)
```
// index.html

<!DOCTYPE html>
<head>
  <.....>
</head>
<body>
  <h1>Block</h1>
  <p><img src='blocking.png'></p>
</body>
```

```
// app.js

app.use(express.static('public'));
```
