## http-logger
A cute and simple middleware for node.js to **write/log** all HTTP requests to a **file**. 

## Usage

```javascript 
var logger = require('http-logger');
```

### logger(options)
 
Create a http-logger middleware function using the given `options`.
The `options` argument must be a object of a predefined properties (see below for the properties).

**All the options are optional**

#### Options

http-logger accepts three properties in the options object.

##### dir 

- Type : `String`
- Optional : Yes
- Default value :'http_logger'

Directory name where you want to log the requests.
Only pass directory name.

e.g. 

```javascript
logger({
dir:'logToThisFolder'
});
```
##### file

- Type : `String`
- Optional : Yes
- Default value :'http_logger'

File name where you want to log the requests.
Only pass file name.

e.g. 

```javascript
logger({
file:'logToThisFile'
});
```
##### dateWise 

- Type : `Boolean`
- Optional : Yes
- Default value :`false`

If set `true` then new log file will generate each day.

e.g. 

```javascript
logger({
dateWise:true
});
```

##### callback 

- Type : `Function`
- Optional : Yes
- Default value :`empty function`

Callback function return logs.

e.g. 

```javascript
logger({
callback:function(log) {
    console.log(log);
}
});
```

##### saveToFile 

- Type : `Boolean`
- Optional : Yes
- Default value :`true`

If set `false` no logs have been written into the file.

e.g. 

```javascript
logger({
saveToFile:'false'
});
```

### Example

```javascript
// Require the ingredients we need
var express = require("express");
var http = require("http");
var logger = require("http-logger");

// Build the app
var app = express();

// Use our middleware
app.use(logger());

// Add some middleware
app.use(function(req, res) {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("Hello world!");
});

// Start it up!
http.createServer(app).listen(3000);
```



