# Course-DeployAngularToHeroku

## Install Server to run your app
Locally we run ng serve from terminal to run our app on local browser. But we will need to setup an Express server that will run our production ready app (from dist folder created) only to ensure light-weight and fast loading.

Install Express server by running:

`npm install express path --save`

Create a **server.js** file in the root of the application and paste the following code.

```javascript
//Install express server
const express = require('express');
const path = require('path');

const app = express();

// Serve only the static files form the dist directory
app.use(express.static(__dirname + '/dist/<name-of-app>'));

app.get('/*', function(req,res) {
    
res.sendFile(path.join(__dirname+'/dist/<name-of-app>/index.html'));
});

// Start the app by listening on the default Heroku port
app.listen(process.env.PORT || 8080);
```

## Change start command
In **package.json**, change the `"start"` command to node **server.js** so it becomes:

`"start": "node server.js"`

Add more:

`"preinstall": ""`

`"postinstall": "ng build --prod"`

Here’s what the complete **package.json** looks like. Yours may contain more depending on your application-specific packages.

```javascript
{
  "name": "demo-deploy",
  "version": "0.0.0",
  "license": "MIT",
  "scripts": {
    "ng": "ng",
    "start": "node server.js",
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e",
    "preinstall": "",
    "postinstall": "ng build --prod"
  }
  ```
