 ---
layout: post
title: "Learnyounode - My First Async I/O"
date: 2014-07-12 15:00:00
videourl: #
categories: learnyounode tutorials
imageurl: https://pbs.twimg.com/profile_images/1437021459/nodejs-dark.png
---
# My First Async I/O!

A walkthrough for the fourth exercise My First Async I/O from the learnyounode program by Founders and Coders team Digital Alchemy. 

# Task
Write a program that uses a single **asynchronous** filesystem operation to read a file and print the number of newlines it contains to the console (stdout), similar to running `cat file | wc -l`.

The full path to the file to read will be provided as the first command-line argument.

# New Terms
    require
    readFileSync
    .toString()
    .split()
    \n

# Script
Hi there and welcome back to Founders and Coders team Digital Alchemys learnyounode tutorials. We will be going through the third exercise My First I/O. There will be a lot of hand holding so this may not be for advanced programmers. 

So lets begin by running learnyounode:

    $ learnyounode

And lets go down to My First I/O and jump in.   

# Task Walkthrough
So, lets take a look at the task. Write a program that uses a single synchronous filesystem operation to read a file and print the number of newlines it contains to the console.

Before we dive in, lets look at the word synchronous. Anyone who has done some background reading on node.js knows that the beauty of node is the ability to run asynchronous functions. So why are we making a program that doesn't take advantage of this? Just to make a point, thats why!

So what do we need? We need to be able to access the command-line input, great we know how to do that. We need to be able to access the contents of a file. We need to be able to search the file for how many newlines it has. 

Now if you head over to the hints section, you will see mention of the fs module. Node installations come packaged with some very useful modules. It is worth checking out the documentation on this. So first we need to tell the computer we require the fs (file system) module. 

    var fs = require('fs')
    
So we have a global variable containing the fs module. Awesome. If you are wondering why we did this, and you can't be bothered to read the documentation, just know that this module gives us access to some of the functions we will be needing for this exercise. Ok, lets get access to our command-line input. We are going to use process.argv but what's our parameter? Well, because we will only have one argument proceeding our file name and that is the one we want we can just ask for position 2.

    process.argv[2]
    
So we now have our file returned to us. But we need to be able to read the file. No problem! The fs module has a readFile function. But this is supposed to be a synchronous process. So we will use:

    fs.readFileSync(process.argv[2])
    
This function will now check the contents of the file and return it as a buffer (an array). Lets give it a variable contents before we continue.

    var contents = fs.readFileSync(process.argv[2])
    
Now we need to read the file for how many newlines it has. This can be a bit complicated. Lets think about some of the functions we've used in previous exercises. One that comes to mind is .length. If you recall, this tells us the number of items in an array. What if we made a new item in our array for each newline? To do that we need to make the entire array a string and then split it back up into an array based on the newlines. So...

    contents.toString().split('\n')
    
Sorry if that was a bit fast. toString will convert the value of our contents variable into a string. .split() will turn the string back into an array, breaking it up based on the contents of its brackets. \n means newline. So whats happening here is the contents array is made into a string, then the string is split at every point where there is a newline (\n) figure in the document. We now have an array with an item for every newline. Well, not quite. There will be an extra item in the array that isn't a newline. The last line of the file doesn't have a newline figure because there is nothing new added after that point. So there is one too many items. Easy fix. We just deduct 1. So using our .length function, and making a new variable lines:

    var lines = contents.toString().split('\n').length - 1
    
Doesn't that feel good? So altogether now:

    var fs = require('fs')
    
    var contents = fs.readFileSync(process.argv[2])
    var lines = contents.toString().split('\n').length - 1
    console.log(lines)
    
You can now try out your program on a file of your choice using:
    
    $ node mynode.js yourfile.extension
    
And you can verify to pass:

    $ learnyounode verify mynode.js
    
And you have passed! Looking at the data in the solution there is a method of avoiding using your .toString() function. Have a read through if you fancy.

So just a quick summary of todays learning. **require** lets the computer know you need a specific module for your code to work. **readFileSync** reads and returns the contents of a file in a synchronous manner. **.toString()** converts the subject of the brackets into a string. **.split()** will convert the subject into an array based on its own parameters. **'\n'** represents a newline and can be used as parameter for .split(). 

Thats all for this tutorial, I hope you will join us in the next exercise, My First Async I/O!