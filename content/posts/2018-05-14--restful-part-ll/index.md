---
title: RESTful API Part II
subTitle: Simple and Elegant
category: "nodejs"
cover: Wolf-quote.jpg
---

In the previous [part]() we went through the mere concept of RESTful API, what it is and what is it used for. In this part we are going to actually build one and when you are done everything will clear up as a crystal.

OK, Let’s Do This!

![Unsplash](./Wolf-quote.jpg)

**Prerequisites**:

1. Code Editor(I use VS Code)
2. Node JS
3. MongoDB (Community Server version)
4. Robo 3T (MongoDB GUI)
5. Postman (For Testing API)

Download & Install them all. Also, we will build API in es2015(or es6) Javascript syntax so make sure you have Babel extension installed in your text editor to compile it to es5.

This was the harder part Actually.

#Step 1 — Setting Up Database

First we need to get our database up and running. Make a database directory wherever you want and then go into directory where MongoDB is installed and start the database from command prompt. It should look something like this:

![Unsplash](./server1.png)

Press enter, You should be connected to port 27017 like this:

![Unsplash](./mongo1.jpeg)

That’s It ! You have now set up a Mongo Database. In our database we will store user info(email and password) like in the most of the web applications is required. During the Development process you have to leave this command prompt like this and start another one for API development.

#Step 2 — Setting up a Server

Make a directory for our API wherever you want and enter it with command prompt as within your text editor(mine is VS Code).
```
cd rest-node-api
```

First we have to setup our package.json file so we can install our dependencies for this project. in the command prompt:
```
npm init -y
```
This will setup our default package.json file which can be seen as ingredients list of our recipe.

Now let’s install Express. The best web framework for NodeJS development.
```
npm i express --save
```

package.json file should look like this:

![Unsplash](./jsonfile.png)

And all of our further dependencies will be shown here like this. OK, Lets set up a server.

Make *server.js* file in your root folder in text editor, require express, make app variable to use express and set up a port where the app will run. It should look like this:

![Unsplash](./server2.png)

Save file and go to command prompt to start the server.
```
node server.js
```
![Unsplash](./server3.png)

One more thing. go to your browser and type in the url window:
```
http://localhost:3000/
```
You should get the message:

![Unsplash](./apibrowser.png)

Everything is set to start our API development.

#Step 3 — Model

>Models are fancy constructors compiled from our Schema definitions. Instances of these models represent documents which can be saved and retrieved from our database. All document creation and retrieval from the database is handled by these models.

To set up our model we need [Mongoose](mongoosejs.com).

>Mongoose provides a straight-forward, schema-based solution to model your application data. It includes built-in type casting, validation, query building, business logic hooks and more, out of the box.

Our Model will be consisted of 2 things:

1. Setting up collection in our database
2. Building Schema for our collection

*Collection and Schema together make Model and will be more cleared up during the building process. So let’s proceed.*

First let’s install Mongoose:

```
npm i mongoose --save
```

Now let’s create 2 new folders: First will be named model with created file: user.js and the Second will be named db with file: mongoose.js. Our root folder should look like this:

![Unsplash](./mongoose1.png)

Open a mongoose.js file and in this file we will open a connection to the Users database on our locally running instance of MongoDB(localhost:27017). Also, we should get notified in our console if we connected successfully:

![Unsplash](./mongoose2.png)

Next we have to set up our User Schema. Schema is a blueprint of our user data and what it will be consisted of:

![Unsplash](./mongoose3.png)

As you can see, our user model is only made of 2 parameters: email and password which will be strings. This is the simplest form of Schema for the purpose of better understanding. Usually, there are more than one Schema in a web application and it’s consisted of many more parameters such as: login time, location, age, credit card number etc.

Now, all that’s left for this section is to import these two files into our main server.js file.

```javascript
//server.js

const {mongoose} = require('./db/mongoose');

const {User} = require('./model/user');
```