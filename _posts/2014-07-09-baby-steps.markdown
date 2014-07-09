---
layout: post
title: "Node.js - Baby Steps"
date: 2014-07-09 11:43:00
categories: node tutorials
imageurl: https://pbs.twimg.com/profile_images/1437021459/nodejs-dark.png
---
This is a tutorial for learnyounode babysteps exercise. Good luck!


    1 var result = 0
    2
    3 for (var i = 2; i < process.argv.length; i++)
    4  result += Number(process.argv[i])
    5
    6 console.log(result)

1: var result = 0 : this declares the variable called result and assigns it the value 0 

3: Declares a for loop.

Statement 1: var i = 2 : this declares the variable called i and assigns it the value 0. More explanation below.

Statement 2: i < process.argv.length : this states the condition of the for loop. In this case the loop should only be run when i is less than the length of process.argv.

process.argv : This is an array representing each thing in the command-line. e.g. ['node', 'babysteps.js', '...']. This gives an explanation now for statement 1. The length of process.argv is at a minimum of 2 if you only run the js and give no arguments. So with at least 1 argument, the for loop will run. Without any arguments the result variable will remain at 0. 

Statement 3: i++ : This means increase the value of i by 1 everytime the loop runs. So if the command-line contains 1 argument the loop will stop after running once as i will have the value of 3 which would be the same as the length of process.argv. If the command-line contains 5 arguments, the loop will run 5 times so that i = 7 which would be the same as process.argv.length. 

4: This is the code block to be executed for each run of the loop. 

process.argv[i] : This has the value of the number in the position i in the array. On the first run of the loop i will have the value 3 which is the first argument in the command-line. If the for loop runs again, i will have increased to 4 which would give the second argument.. etc. 

Number() : this function converts an object to its number value. e.g. Number(true) = 1, Number('4') = 4 etc. so Number(process.argv[i]) will convert the argument from a string to a number value. 

result += Number(process.argv[i]) : this will add the value of the argument to the value of the result variable and reassign the result variable to the resultant value of the 2.

console.log(result) : I'm not telling you what this does. 

