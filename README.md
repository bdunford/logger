# logger

A logger for node Express that can be used for logging requests.

Requires Nodejs http://nodejs.org


## Installing

__From the Command Line__<br />
npm install git+https://github.com/bdunford/logger.git

__package.json as a dependency__<br />
add "logger": "git+https://github.com/bdunford/logger.git" to dependencies <br />
```json
{
    "name": "your-app",
    "version": "0.0.0",
    "private": true,
    "description": "just another node app",
    "dependencies": {
        "logger": "git+https://github.com/bdunford/logger.git"
    }
}

```
__Raw__<br />
```git clone https://github.com/bdunford/helpers```<br />
Be sure to run npm install from with in the __logger__ directory


## Usage

require loger in your javascript.
```javascript
var logger = require('logger');
```

Logger is best used with express middleware. and has two methods _"for now"_
```javascript

var app = express()

app.use(function(res,req,next){
    logger.info(res,"your-app");
    next();
})

/* will write to the console
INFO >>> APPLICATION: your-app
REQUEST >>> METHOD: GET  PATH: /text/  REMOTE: 127.0.0.1
HEADERS >>> {"user-agent":"browser"}
QUERY >>> {format: "json"}
BODY >>> {name: "fred", age: 4, mood: "happy"} // requires body parser
*/

app.use(function(res,req,next){
    logger.warn(res,"something is wierd","your-app");
    next();
})

/* will write to the console
WARNING >>> APPLICATION: your-app  MESSAGE: something is wierd
REQUEST >>> METHOD: GET  PATH: /text/  REMOTE: 127.0.0.1
HEADERS >>> {"user-agent":"browser"}
QUERY >>> {format: "json"}
BODY >>> {name: "fred", age: 4, mood: "happy"} // requires body parser
*/

```
