<img src='http://dailyjs.com/images/posts/browserify2.png'>
Browserify!

What is it?

Browserify enables your front end app to use the common JS module system, the same that you see in node apps. With Browserify, you can install front end dependencies with NPM.

####Get started:

Start up a new directory
```
npm install -g browserify
npm install -g watchify
npm install --save <your packages>
```

####When to use?
- Browserify is really good for games
- File organization
- Preventing information bleeding into the global scope
- Applications that share front end and back end dependencies
- When you don't have structure from a framework like Backbone or Angular.

####Let's create a demo app!

1. Create a directory called browserifyTest and then run npm init:

2. Add a folder called app with add.js and app.js in it.

3. Create an index.html in the root directory.

4. Your directory should look like this:
```
//Directory:

browserifyTest
|
 –––– app ––– add.js
|     |
|      –––––– app.js
| 
 –––– index.html
|
 –––– package.json

```
From your console, run the following command:
```
npm install browserify
```

Edit your package.json by adding the following lines of code to your script area:
```
{
  "name": "browserifyTest",
  "version": "0.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "browserify app/app.js > bundle.js",
    "watch": "watchify app/app.js -o bundle.js"
  },
  "author": "",
  "license": "ISC"
}
```
What this does is give npm some commands it can run. The build script concatenates all your app files into a bundle.js.

The watch script watches for changes in your app file and will rebuild the bundle.js when changes occur.

In your console enter the following command:

```
npm run watch
```

You should see a bundle.js file appear:

Lets now populate our app.js and our add.js files:
```
//app.js
'use strict'

var add = require('./add');

console.log(add(1,2));
```

```
//add.js
'use strict';

var add = function(a,b){
  return a + b;
}

module.exports = add;
```


Now in your index.html
```
<!DOCTYPE html>
<html>
<head>
  <title>Browserify Test App</title>
</head>
<body>
<script type="text/javascript" src='./bundle.js'></script>
</body>
</html>
```

If you open this page in the browser, and then open your console, you will be able to see 3 being logged.

Browserify Magic!!!