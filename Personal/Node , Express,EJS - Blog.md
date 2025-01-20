
## create env and .gitignore
the .env file will contain all the all variables that hold senstive data.
.gitignore files will holds folder and files that github will ignore when code is stored inside github.
# 1- Setting express server

```node 
// adding env file
require('dotenv').config();
// importing express js
const express  = require('express');
// creating the app
const app = express();
// adding port
const PORT = 4000 || process.env.PORT;
//using express layout
const expressLayout = require('express-ejs-layouts');

// creating end point
app.get('',(req,res)=>{

    res.send('helo');

});
  
//listing port
app.listen(PORT, ()=>{

console.log(`App Runing on port ${PORT}`);

});
```


## 2- sperate server from the main file.
in the app.js file write the following
```node
require('dotenv').config();

const express  = require('express');
const app = express();
const PORT = 4000 || process.env.PORT;
// helps for the layout of the ui
const expressLayout = require('express-ejs-layouts');
// this import is helping to not include the public folder when every we need to access folders inside the public folder
app.use(express.static('public'));

// Template engine

app.use(expressLayout);

app.set('layout','./layouts/main');

app.set('view engine','ejs');

// including server file inside server folder file is called main.js

app.use('/',require('./server/routes/main'));
app.listen(PORT, ()=>{

console.log(`App Runing on port ${PORT}`);

});
```

then create folder named server and inside of it create file named routes and create file named main.js that will hold all the routes , write the code below in main.js

```node
const express  = require('express');

const router = express.Router();
router.get('',(req,res)=>{

    //data

    const locals = {

        title:'MuradCade-Blog',

        description:'simple blog created with nodejs,express and mangodb'

    }

    // passing data into page using ejs

    res.render('index', {locals});

});

module.exports = router;
```


## 3- create place that will hold the pages/templates
create folder named views and inside of it create folder called layout inside the layout folder create file named main.ejs , also create file inside the views folder called index.ejs.

## 4- create place that will hold all the assets such as images/css/js.
create folder called public , this folder will hold all related assets such as images/css/js


## Connecting to mangodb using nodejs
the code blow shows how to connect to mangodb.
```node
const mangoose = require('mongoose');
const connectdb = async()=>{
    try {

        mangoose.set('strictQuery',false);

        const connect  = await mangoose.connect(process.env.MANGODB_URL);

        console.log(`database connected ${connect.connection.host}`);

    } catch (error) {
            console.log(error);
    }
}

  
  

module.exports = connectdb;
```

## create model in mangodb
in order to store data inside mangodb you will need to create model(table), code below show how to create model
```node
// this file contains the table that will store the posts

const mongoose = require('mongoose');
// schema is the database build (building the attributes of the pots table )
const schema = mongoose.Schema;
const postschema = new Schema({
 // attribute 1
 title:{
	type:String,
	required:true,

 },
 // attribute 2
 body:{
	type:String,
	required:true,},
 // attribute 3
 createdAt:{
	type:Date,
	default:Date.now

 },
 // attribute 4
 updatedAt:{
	type:Date,
	default:Date.now
},

});
// expoerting the schema (the name posts inside the model is made up name , you can named what you want)

module.exports = mongoose.model('Posts',postschema);
```

## inserting data to model using node js

```node

// importing the model for that specific insert

const post  = require('../models/post');
// insert data into the post table

function insertpostdata(){
    post.insertMany([

        {
	title:'building web application like pro',
	 body:'in this post you will learn how to build simple blog webapplication using node,express,mangodb and an ejs'

        }

    ])

}

  
  

insertpostdata();
```