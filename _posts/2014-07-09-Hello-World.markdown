---
layout: post
title: "Learnyounode - Hello World!"
date: 2014-07-09 13:15:00
categories: learnyounode tutorials
imageurl: https://pbs.twimg.com/profile_images/1437021459/nodejs-dark.png
---
# Hello World!

An introduction to Founders and Coders and team Digital Alchemy. A brief walkthrough for the learnyounode program for learning node.js. A walkthrough for the first exercise HELLO WORLD

# Task
Write a program that prints the text "HELLO WORLD" to the console (stdout).

# New Terms
    $ learnyounode
    $ node program.js
    console.log(“text”)
    $ learnyounode verify program.js

# Script
Welcome to Founders and Coders team Digital Alchemy’s learnyounode walkthrough. This series of tutorials will take you step by step through each learnyounode exercise, explaining each term in detail. There will be a lot of hand holding so this tutorial may not be for advanced programmers.    

I’m using Nitrous.io for my development environment and I have already cloned the learnyounode files from its github repository into my box.    

The first term we will type into the console on the command-line is:

    $ learnyounode

This runs the learnyounode program. As you can see on screen there are 13 exercises to be completed. We’ll jump straight into Hello World. What comes up now in the console is the task at hand, a series of hints and then some learnyounode functions that you can run.     

# Task Walkthrough
Fortunately this is a simple enough task. In the hints section we are even told pretty much what we need to put in our file. 
So, I’ve made a file called mynode.js and I am going to type into the first line:

    console.log(“HELLO WORLD”)

This really is very basic javascript, but I will still go through the line to ensure there is no confusion. Console.log() prints the contents of the brackets into the console. By print I mean it just types it out for us in the console, you don’t need a printer! Inside the brackets is what we call a string. A string is just raw data inside speech marks. Strings can be numbers, items, letters… whatever you like. In this case our string is HELLO WORLD. So now I save the and I can run it in the console on the command line using:

    $ node mynode.js

This is the function node uses to run your script. As you can see the console now contains our string HELLO WORLD. Congratulations, we did it! With a program this simple we can walk away from here. However, your scripts will become more complicated, especially during these exercises so it is worth using the verify function:

    $ learnyounode verify mynode.js

What you see here should be idiot proof. If it doesn’t make sense, and you are certain you’re not an idiot, please feel free to direct all complaints to any brick wall in your neighbourhood. Looking at the format we can see the result of running our code, the expected result if our code should work, whether we passed or failed and if we did pass we are shown the official solution to the exercise.     

So just a quick summary of todays learning. $ learnyounode runs the learnyounode program, console.log(“”) prints out a string to the console. $ node mynode.js runs the program mynode.js and $ learnyounode verify mynode.js verifies the program works using learnyounode own files and parameters.    

Thats all for this tutorial, I hope you will join us in the next exercise, Baby Steps!
