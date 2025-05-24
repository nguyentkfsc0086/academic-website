---
title: Statistics using R with Biology Example
date: 2025-05-24
tags: 
    - Statistics
    - Computer Science
    - Bioinformatics
---
This is my learning notes from the book Statistics using R with Bio Example. 
I'm really interested in the field Bioinformatics so this is a good begining way to start with it!
## Basic of Working with R
### Using the S Languague
R is based on another languague name S.
R can be an implementation of S or an indepedence language or a software package
S and R are designed for statistical programming and it is considered high-level object-oriented statistical programming language. And this is not the same as Object Oriented Programming Language (OPP) likes C++ or Java. We will not discuss about OPP in this course, if you are interested check this [link]('https://www.techtarget.com/searchapparchitecture/definition/object-oriented-programming-OOP#:~:text=Object%2Doriented%20programming%20(OOP)%20is%20a%20computer%20programming%20model,has%20unique%20attributes%20and%20behavior.')

Everything about R is about create and operate objects. There is 2 types of object, ***function objects*** and ***data objects***
Data object: An object that hold the data that we assigned
Function object: An object that perform tasks on data object, it can be import from a package or written from scratch. Some popular tasks that function object do is calculation, graphical presentation,....
### Structuring Data with Object

There is 2 ways to work with data in R: 
    &emsp;&emsp; - Directly: import from the keyboard 
    &emsp;&emsp; - Indirectly: import through a file

We can create our form of data object (data structure) if needed for the job. But R has a set of standard data: \
    - Scalar \
    - Vector \
    - Factor \
    - Matrix \
    - Array \
    - List \
    - Data frame\
The different types of data object handle different types of data (characters, numerics,...)
Data objects generally have **3 properties**: \
    - Type: One of the data forms that we mentioned above \
    - Value \
    - Name \
Sometimes we don't need to define the name of the object but we should always provide a comment that explain about the name of the objects
### Type of data objects in R
**Scalar**
This is the simplest type of an object. \
A scalar is an object with 1 value. To assign a value to a variable, we can use the assignment operator '<-'. The '=' sign will be use for a different task \

Example:
```R
#Create a scalar data with the name x and the value 4
x <- 4
#Create a scalar data with the name y and the value 5
y <- 5
```

