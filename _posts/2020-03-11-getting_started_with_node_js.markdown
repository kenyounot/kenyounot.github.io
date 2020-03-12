---
layout: post
title:      "Getting Started With Node.js"
date:       2020-03-11 23:42:17 -0400
permalink:  getting_started_with_node_js
---


I've always been a fan of JavaScript, and what better way to expand on my skills than to learn a backend technology also written in JavaScript. I started learning  Node.js last week so I'm definitely still a newbie but still wanted to share my experiences while learning this cool serverside technology. First I'll walk through what node is and why it's different than my first love Ruby on Rails, and then I'll dive into how to get started on getting your first Node.js app set up. I will expand on this further in future blog posts. 

So what is Node? Node solves a problem. It allows you to run JavaScript outside the browser in its own runtime environment. What this allows you to do is create server side applications or my personal favorite REST API's using JavaScript. Why use Node over say Rails? In my opinion if you're looking to setup an application and performance and scalability is a priority for you, Node is the way to go. Node is non-blocking which means when we hit a function in our application that will take an extended amount of time, instead of waiting for that function to finish, it will come back later to get what it needed from that function. This means we get an incredibly fast solution to server side applications.

Enough with the boring talk, lets get a Node.js up and running. The first thing we want to do is create a new directory for our project. Then cd into that directory and in the terminal run the command ```npm init``` for now don't worry about the prompts that follow, these will the parameters that make up your package.json file. Now lets open up our directory in our code editor. The first thing we are going to do is install a dependecy called Express. Express in a nutshell let's you create your endpoints in a simpler way. Let's install this dependency by running the command ```npm install --save express```. Now if we open our package.json file we will see express is listed as a new dependecy. 

So now that we have our dependencies lets create a new file called 'server.js' you can call this whatever you want but I like calling it server. In the server.js file the first line we are going to write is going to be ```const express = require('express')```, what this does it allows us to import the express module and store it in a variable called express. Next, let's create a variable called app and set it equal to the default function exported by express. ```const app = express(); ``` this allows us to create a new instance of express to call for our application. Now we need to set our default port where our app will listent to requests. ```const port = 5000```. Okay, now we are ready to finally set up our first route handler. Let's call app.get() which is telling app to call this function when we recieve a get request. The first argument of this function asks for a route to match that get request. so ```app.get('/')``` would respond to a get request to the '/' path. Next we need to tell the app what to do when we reach this route.
```app.get('/', (req, res) => {
                  res.send({
									    hi: 'there'
									})

}```

We are passing in the req(request) parameter that we aren't using now but contains important information coming in from the request including headers. The res(response) argument is what we respond to the request. Here we are responding with an Object that contains hi there. Finally lets set our app to listen to the port we defined earlier. 
```app.listen(port);```

and now run the command ```node server.js``` or whatever you named your file and then go to 'localhost:5000' and tada youve created your first Node.js app! Here is what the final code should look like. 

```
const express = require('express');

const app = express();
const port = 5000;

app.get('/', (req, res) => {
	res.send({
		hi: 'there'
	});
});

app.listen(port);
```


