---
layout: post
title: Let's Build a Basic SocketIO Application
---

Welcome back! This post will be all about how to create a very basic Socket IO Application. A few weeks ago, I was assigned a project in class to create a basic chat application hosted on Cloud 9 which used Python Flask and Socket IO.
When I was doing some basic research on how to get started, I found that it was very difficult to find a good tutorial that kept everything simple, and was easy to follow. Because of this, I figured that this would be a perfect subject for my first technical blog post.

GOAL: The goal of this post is to provide a step-by-step tutorial to create a very basic Socket IO Application. 

In the screen-shots included to supplement this tutorial, I will be using Cloud 9 to host my application, Javascript to execute the Socket IO functionalities, and Python Flask for the server-side code. Knowledge of the previously mentioned tools are not necessary but certainly wouldn't hurt. 

If you finish the tutorial and want to further your knowledge on Socket IO, there is plenty of documentation and examples also available [here](http://socket.io/docs/).

Let's Get Started:

I'm starting with a brand-spanking-new Cloud 9 workspace, to limit confusion when you guys are following along. Feel free to do the same in order to help relate your app to the screen-shots provided.
The first thing we are going to want to do is install flask and SocketIO using the commands:

sudo easy_install flask
![_config.yml]({{ site.baseurl }}/images/1.png)


and

sudo easy_install flask-socketio
![_config.yml]({{ site.baseurl }}/images/2.png)


When you get those installed properly, you should get results like you see in the pictures above.

Now, let's set up our python server file. Copy the code shown below and save it in your project file with the title "server.py":
![_config.yml]({{ site.baseurl }}/images/3.png)

And get the rest of our files in place, so that we can run the server and get an HTML page to load without errors. First, we're going to need a folder named "static" and another named "templates" inside of our project file. Then, inside of "static" we need to create a folder named "js" where we will store our Javascript code. If you have any confusion about the directory structure, just refer to the picture below.


![_config.yml]({{ site.baseurl }}/images/4.png)

Next, we need to create our index.html file. We will keep it very simple, because the main focus of this tutorial is the SocketIO and the HTML page just gives us a medium to display our working SocketIO code. 

Create your "index.html" file inside of your "templates" folder, and add the code shown below.


![_config.yml]({{ site.baseurl }}/images/5.png)


This will give us a way to display the "messages" that we send through our app. I will explain the code itself a little bit later. For now, take note of the line: <html ng-app="simpleSocketIO"> This line tells the HTML template that some part of it will be populated using Angular(ng)JS(Javascript). 

Now, we can finally get into the nitty gritty part of SocketIO: The Javascript. First, let's create a new file in the "js" folder that we created earlier and call it "controller.js". Then, enter the code shown below:
![_config.yml]({{ site.baseurl }}/images/6.png)

Now, let me give you a quick run down of what any of that means!
Part 1: 
var simpleSocketIO = angular.module('simpleSocketIO', []);  
Here, we are created the angular application. Remember the line from the index.html file I told you to take note of? Here is where we define THAT application so that we can use it in the HTML code. I went out of order a little bit, but I did it so that we could focus on the Javascript code all at once! The "angular" part we imported in server.py. (Don't believe me? Go check!) and the empty brackets are where we would put any dependencies that we might have. We don't need to worry about that for our purposes.

Part 2: 
statTrackChat.controller('ChatController', function($scope){
   var socket = io.connect('https://' + document.domain + ':' + location.port + '/ssio'); 
Here, we are creating the controller. The controller is the middle man between the user and the application. It makes the updates to what we are seeing on the HTML page. We have named ours "ChatController", it works using the "function"s that we define for it, and those functions use the "$scope" defined in our file. The next line, var socket = io.connect('https://' + document.domain + ':' + location.port + '/ssio');, connects our controller back to our server.py file by: 1) defining the domain created when we run our server, 2) the port used when we run our server, and 3) the namespace that we'll use in accordance with our server('/ssio').

Part 3: 
$scope.messages = []; 
$scope.text = '';
These are pretty simple lines, which just define these two variables within the scope of this file. 

NOTE: At this time, go back and look at index.html (remember when I said I'd come back to this?) and take a look at the following lines: 
<script src="static/js/controller.js"></script>
This line tells "index.html" that the Javascript code we'll use with the angular app is located in "static/js/controller.js"

<div class="container" ng-controller="ChatController">
This line tells "index.html" which controller we'll be using to update the data in the file. We have to let it know which controller we are using because it's possible to use multiple controllers within one application!

Now, back to controller.js:

