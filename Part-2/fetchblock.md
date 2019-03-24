## Fetching a list of block 
- loading data from Express with Ajax calls
```
        ------ Request to/ ------>
        <-------------------------
client  ---- Ajax to / block ---->    server
        <-------------------------

```

**Adding client-side javascript**
- place all files under the public folder
```
// index.html

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset = "UTF-8">
    <title>Building Blocks</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <h1>Blocks</h1>
    <ul class="block-list"></ul>
    
    <script src="jquery.js"></script>
    <!-- jquery to help manipulate the DOM and simplyfy Ajax calls -->
    
    <script src="client.js"></script>
    <!-- client.js is where custom client-side code that will talk to the express API-->
    
  </body>
</html>
```

**Making Ajax calls**
- request to /block, then append results to /block endpoint
```
// client.js



```

**Responding with JSON**
- create a new route for the /blocks endpoint
```
// app.js


```
