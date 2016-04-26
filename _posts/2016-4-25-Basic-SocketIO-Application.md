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

Now, let's set up our python server file:
![_config.yml]({{ site.baseurl }}/images/2.png)

And get the rest of our files in place, so that we can run the server and get an HTML page to load without errors.


