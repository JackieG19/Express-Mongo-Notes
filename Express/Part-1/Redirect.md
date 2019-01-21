**Redirecting to relative path**

The redirect function sets the proper response headers.
```
aap.get('/block', function(req, res){
// to redirect requests to the new /parts route
  res.redirect('/parts');
  // passing in the destination path as the argument
});

// so when the request comes in for /blocks, 
// the application's going to respond with a redirect to /parts
```

Request:
- $ curl -i http://localhost:3000/blocks
```
HTTP/1.1 302 Moved Temporarily
X-Powered-By: Express
Location: /parts
content-Type: text/plain; charset = uft-8
```
Moved temporarily. Redirecting to /parts

___

**Redirecting with custom status code**

The status code ca be passed as the first argument to redirect.
```
app.get('/blocks', function(req, res){
  response.redirect(301, '/parts');
  // 301 = moved permanently
}):
```
