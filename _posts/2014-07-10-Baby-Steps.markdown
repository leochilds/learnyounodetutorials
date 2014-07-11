---
layout: post
title: "Learnyounode - Baby Steps"
date: 2014-07-10 13:15:00
videourl: #
categories: learnyounode tutorials
imageurl: https://pbs.twimg.com/profile_images/1437021459/nodejs-dark.png
---
# Baby Steps!

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

So lets consider what we need for this task. We need a result to print out to the command line. We get this result by adding arguments from the command line so we need to be able to access these somehow, and we need to ensure the program can handle any amount of arguments in the command line. So just adding 2 arguments won't work if we put in 3 nummbers.

Lets go back and start with the variable function:

    var result = 0
    
Here we are declaring a global variable. More about global variables in another exercise. The variable is being called result, and the value it has been assigned for now is 0. Why? Because if no numbers are run with the program, the result should be 0. Its a starting point. Next lets have a look at how we can access the command line. If you check the hints in learnyounode there is mention of:

    process.argv
    
This is an array representing each thing in the command-line. e.g. ['node', 'babysteps.js', '...']. An array is basically a list of items, seperated by commas inside square brackets. So if I typed: 

    $ node mynode.js 1 2 3 4 

process.argv would represent this as ['node', 'mynode.js', '1', '2', '3', '4']. We can access specific parts of an array using square brackets at the end. For example process.argv[1] would give me the string 'mynode.js'. Why does 1 not deliver 'node'? Because the first term is represented by the number 0.    

So now what we want to do is take the number arguments from our process.argv and add them to the result variables value. We know we can specify that we want the arguments starting from process.argv[2] until the array ends. But how do we know when it ends? With the .length function of course:

    process.argv.length
    
This returns the number of terms in an array as a number. So for our example above there will be 6 terms. We know know how long it is. So... we want to take the number arguments, add them to the result and stop when we have used all of the numbers. It sound like we need a for loop:

    for (statement1; statement2; statement3)
      code to be executed
      
The for function takes 3 parameters, and based on that carries out the code that needs to be executed. So usually, statement1 is a variable assignment, statement2 is a condition to run the code, and statement3 is some code to run on each loop to ensure it eventually stops. If your condition can always be true the program will run forever and you could crash your machine! I'm going to fill these in to what they need to be then explain further:

    for (var i = 2; i < process.argv.length; statement3)
      code to be executed
      
In the first statement I have made the variable i and given it the value of 2. I'll explain more later. Next I have declared that for this code to run the value of i must be smaller than the length of our input in the command line. Lets think about this a bit more. If I input $ node mynode.js into the command line, there will be no arguments. So the length will be 2. By starting my i value at 2 I am telling the computer not to run my code as there are no arguments. If I enter one of more arguments, the length of my input will be greater than 2 and my process will run. But how do I stop it? 

    for (var i = 2; i < process.argv.length; i++)
      code to be executed
      
I've now added my statement to ensure the loop closes. i++ will add 1 to the value of i everytime the code is executed. Lets use an example to demonstrate. I run:

    $ node mynode.js 1 2 3 4
    
The computer goes through my code. Firstly, i has the value 2. Thanks. Is i less than the length of the input? The input length is 6 so yes. Add the value of 1 to the currently assigned value of i. i now has the value 3. Execute code block. Is i less than the process length? The input is 6 so yes. Add the value of 1 to the currently assigned value of i. i now has the value 3. ...etc

Eventually, the value of i will reach 6, so the code will run 4 times, once for each argument. Then the code will stop. Great, except we still haven't told the computer what to do if the condition is true. We want to add each number argument to the result variable. So how can we select the numbers from the console. By using process.argv[]. So for the first execution we want to take the first number which is the 3 item in the array. By using the square brackets that would be position 2 (starts at 0 remember). So:

    process.argv[2]
    
But then what about the other numbers? Well why don't we use i? i starts at the value 2 and increases everytime the code is run, so the code will sequentially run through each argument starting from position 2 until there are none left!

    process.argv[i]
    
Yay! We can now select each number. But there is still no instruction! Lets add the number to our result variable.

    result += process.argv[i]
    
Using += we are first adding the two values and then we are assigning the new value to our result variable. Awesome, we are now adding the string in position i of our input to the result variable. Wait, the string? We don't want that, we want a number value. So we can use the Number() function. This function returns the number value of its contents. For example:

    Number(true);
    Number(12);
    
Would produce:

    1
    12
    
So altogether now:

    var result = 0
    
    for (var i = 2; i < process.argv.length; i++)
      result += Number(process.argv[i])
      
    console.log(result)
    
First we declare the variable result and give it a value 0. Next we start a for loop, declaring the variable i to start with the value 2, stating to only run the code if the length of the input is greater than our i variable. If the condition is true, add the Number value of the argument in position i to the result variable and then increase the value of i by one. The for loop will then run again until the variable i has the same value as the length of the input. 

When our for loop has stopped we use our trusty, console.log() to print the value of the result variable into the console. The content of the console.log() function is not a string in this case, it is a variable which can be a string (or anything else for that matter). Save and run:

    $ node mynode.js 5 6 3 7
    result==>21
    
We can also now verify using:

    $ learnyounode verify mynode.js
    
And you have passed! 

So just a quick summary of todays learning. **var** delcares a variable and we assign it a value. **for** loops run code based on specified conditions. **process.argv** returns an array of the items inputted into the command-line. **process.argv[]** returns the item in the position specified between the square brackets. **.length** gives us the number of items in the array. **++** adds 1 to a variable **+=** adds a specified value to a variable and reassigns it. **Number()** returns the number value of its contents.

Thats all for this tutorial, I hope you will join us in the next exercise, My First I/O!
