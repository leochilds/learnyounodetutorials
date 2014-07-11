---
layout: post
title: "Learnyounode - Baby Steps"
date: 2014-07-10 13:15:00
videourl: http://dacamden.co.uk/videos/Learnyounode%20Walkthrough%20-%20Baby%20Steps.mp4
categories: learnyounode tutorials
imageurl: https://pbs.twimg.com/profile_images/1437021459/nodejs-dark.png
---
# Baby Steps! draft

A walkthrough for the second exercise Baby Steps from the learnyounode program by Founders and Coders team Digital Alchemy. 

# Task
Write a program that accepts one or more numbers as command-line arguments and prints the sum of those numbers to the console (stdout).

# New Terms
    var
    for
    process.argv
    .length
    ++ and +=
    Number

# Script
Hi there and welcome back to Founders and Coders team Digital Alchemys learnyounode tutorials. We will be going through the second exercise Baby Steps. True to the name there will be a lot of hand holding so this may not be for advanced programmers. 

So lets begin by running learnyounode:

    $ learnyounode

And lets go down to Baby Steps and jump in.   

# Task Walkthrough
So, lets take a look at the task. The task is to write a program that accepts one or more numbers as command-line arguments and prints the sum of those numbers to the console. 

We need to be able to access comand-line arguments input by us. We need to add only the number arguments that precede our program name. We need to be able to add as many numbers as are entered. So lets consider how to access the command-line from our script. If you checkout the hints there is mention of the function **process.argv**. This returns the items in the command line back as an array. So I'll demonstrate with mynode.js file. Entering:

    console.log(process.argv)
    
Save and run:

    $ node mynode.js
    
I get back in my command line:

    [ 'node', 'mynode.js' ]
    
I actually get back [ 'node', '/home/action/learnyounode/mynode.js' ]  which shows the full directory. But thats not important for now. Demonstrating with numbers:

    $ node mynode.js 1 2 3 4
    
I get back:

    [ 'node', 'mynode.js', '1', '2', '3', '4' ]
    
Now we need to be able to access specific parts of this array. We have no interest in using the 1st or 2nd item, so only items preceeding this will be useful to us. Items in an array can be access by passing a parameter through the function. For example in our previous example I could type:

    process.argv[2]
    
This would return the string '1'. Now you probably have noticed that '1' is in the third position in the array. That's because the first value is represented by 0 for many reasons that we don't need to cover in this exercise. Put simply, it make many processes easier to run. Problem is we want to be able to work with all the numbers in the array at some point. So we really should make a variable. What's a variable I hear you ask? Well its a value that can vary depending on what value we assign it. Lets use i. Why i? Because the official solution uses i... that is my only reason.

    var i = 2
    
So this var function declares the variable i exists and then the = function assigns the variable i with a value. In this case it is the value 2. This can be a number, a string, even a function. Javascript is very open about this. How kind. Why 2? Because we have just established that teh first number we are interested in can be access with the parameter 2 in the process.argv function. So we have access to the command-line. We have access to specific parts of the command-line, and we have a variable representing each position. Kind of. Its almost time to introduce the for loop. Loops are handy, if you want to run the same code over and over again, each time with a different value. That sounds like something we want to do. We would like to add each number in turn to get a result. So before we make a for loop, lets make a result.

    var result = 0

So, assuming no numbers are entered, we have a result of 0. Someone to start. Now the for loop. So here is the syntax of the for loop:

    for (statement1, statement2, statement3) {
      code to be executed
    }

Let me explain. Statement1 is the first bit of code considered. It is usually a variable. Statement2 is the condition on which we should run the code, which would probably reference the variable in statement1. Statement3 is code to run after the code to be executed has indeed been executed. So statement3 only runs if the condition is true and it runs after the code block. Very useful stuff. I'm going to go ahead and fill in statement1 and 2:

    for (var i = 2, i < process.argv.length, statement3) {
      code to be executed
    }
    
"What is that!?!?!" You scream. Maybe that's a tad bit dramatic, but you probably are wondering what the .length is is our code. .length is a fancy function that returns the length of its subject. In the case of an array, this is the amount of items in the array. So in our previous example there were 6 items in our array. Let me show you:

    console.log(process.argv.length)
    
Save and run:

    $ node mynode.js 1 2 3 4
    
Returns:

    6
    
See, isn't that scary is it? So lets go back to our for loop and consider what I've done here. First is our variable i, which starts at value 2. As we know, this is our way of making sure we can ignore the first 2 items in our array. Next is the condition, the value of i must be less than the length of the array. So what does this mean? Well, apply some mathematical logic and you should realise that this means the code can only run if we have number arguments. If there is 1 number argument, the length of the array will be 3, which is greater than our i value of 2. If there are no number arguments, the length is 2 and this isn't greater than i so its a no go. This is still incomplete. We want to run our code block on each value sequentially. Furthermore, we want some code to run. Lets write some code to run:

    for (var i = 2, i < process.argv.length, statement3) {
      result += process.argv[i]
    }
    
Lets look at +=. This means add the value of the result to the value of process.argv[i] and then reassign the value to result. So effectively, increase result by the number in positon i. That's all well and good except, the number at position i is not a number. It's a string. I promise, it really is. So we need to turn it into number that we can do math with. Lets use the Number() function.

    for (var i = 2, i < process.argv.length, statement3) {
      result += Number(process.argv[i])
    }

This returns the number value of its argument. So if the argument is '3' then it will return the number 3. If the argument is true then it will return the number 1. You get the picture. So at the moment our for loop checks if i is less than our process.argv length, then if it is, our for loop adds the number in the i position to our result variable. Right now that means it's only going to add the first number because i is still 2 and nothing has changed that. Bring on statement3:

    for (var i = 2, i < process.argv.length, i++) {
      result += Number(process.argv[i])
    }
    
i++ will add 1 to the value of i. This has two effects. Firstly, it allows us to cycle through each argument. After every code execution i increases in value and the subject returned by process.argv[i] changes to the next item in the array. So our loop cycles through each item, adding it to the result variable. The i++ also gives our loop a closing point. Eventually i will reach the same value as the length of the process.argv array, which is entirely deliberate. That way, the condition in statement 2 will no longer be true at the same time that we have ran out of number arguments. Not closing loops can be dangerous, leading to computer crashes in the worst of cases. So lets put all our code together and have a look:

    var result = 0;
    
    for (var i = 2, i < process.argv.length, i++) {
      result += Number(process.argv[i])
    }
    
    console.log(result)

You can now run your program using different number arguments to convince yourself it works.

    $ node mynode.js 4 7 2 8
    
Returns:

    21
    
You can truly convince yourself by running the verify program:

    $ learnyounode verify mynode.js
    
And you have passed! 

So just a quick summary of todays learning. **var** delcares a variable and we assign it a value. **for** loops run code based on specified conditions. **process.argv** returns an array of the items inputted into the command-line. **process.argv[]** returns the item in the position specified between the square brackets. **.length** gives us the number of items in the array. **++** adds 1 to a variable **+=** adds a specified value to a variable and reassigns it. **Number()** returns the number value of its contents.

Thats all for this tutorial, I hope you will join us in the next exercise, My First I/O!
