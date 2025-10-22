# node
is a run time

### install project
```
npm init // init your npm project
// npm ask you bottom question
package name:
version:
description: 
entry point: 
test command:                                                                                                                                                                                                              
git repository:                                                                                                                                                                                                            
keywords:                                                                                                                                                                                                                  
author:                                                                                                                                                                                              
license: (ISC)   
```

**NPM :** Node Package Manger

#### save-dev
It is used for development time dependencies and at release time this dependency does not exist for the project output.

```
npm i chalk --save-dev // put chalk in devDependencies

npm un chalk // this make uninstall package 

npm list --depth=0 // show all installed package

node main.js // load your file

npm outdated // show old installed package

npm i -g // install global package
```

### nodemon
for automat save and run js code
```
npm install -g nodemon // install

nodemon \.main.js // run nodemon on file main.js

rs // restart

nodemon -e html .\main.js // make reload for html
```

when ypu init your project just go to your package.json and add 
```json
  "scripts": {
    "start": "nodemon yourfile.js", // this line and go to terminal and write npm start
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

**point :** for exist in terminal form nodemon first **ctrl + c** next write **clear**

### script package json
```json
 "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "nodemon -e js,html,json main.js",
    "toplearn": "nodemon -e js,html,json main.js",
  },

// for run start script 
npm start

//for run toplearn script
nom run toplearn
```

**point :** if Intilisens is not recognized you can use bottom command :
```
npm i @types/node --save-dev

npm install @types/node@13.13.5 --save-dev
```

### process
```js
console.log(process.title); //what are you running on?
console.log(process.pid); //the pid of the process you have
console.log(process.arch); //the structure of the operating system
console.log(process.version); //version node
console.log(process.platform); //what operating system is the user using?
```

### Router and Filter
```js
// in main file
const adminRoutes = require('./routes/admin');
const app = require('express');

app.use("/admin",adminRoutes); // '/admin' is filter and when you create route. it's by defult put /admin after domain

// in file admin
const express = require('express');

const router = express.Router();

router.get('/',(req,res)=>{ // this route make localhost:3000/admin
    res.send('<h1>Admin</h1>')
});

module.exports = router;
```