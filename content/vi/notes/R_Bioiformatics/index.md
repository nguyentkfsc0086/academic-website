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
R is based on S - another programming language. \
R is a high level statistical object oriented language != OOP\
There is two types of object in R:
- Data object: variable name that hold values
- Functional object: do operation on data object
### Structuring Data with Objects
The way to work with data is entering data - directly and undirectly \
We can create our own data type as needed \
R has a set of available data type:
- Scalars
- Vectors
- Factors
- Matrice and Arrays
- List 
- Data frame

And data objects have 3 properties:
- Type: Scarlar, Vectors,...
- Value: The value of the data
- Name: Should be assigned by an relevant name (num1,....)

Type of data can be understand as data structure
### Type of data in R
**Scalar**\
	Scalar is an object that hold with 1 value and can be assign with "<-"\
Example:
```R
> #create scalar data object x with value 5
> x<-5
> #create scalar data object y with value 2 
> y<-2
```
Mode = data type. \
3 modes of data:
- Numerical
- Character: should be enclose by quotes (double or single)
- Logical

**Vectors**\
The most used object. Can be define as a set of scalar.
- Work the same as arrays (in other langs)
- Data value need to be the same mode but can store any mode of data

There is a few ways to enter values into vectors:
- c() function
- scan() function
```R
myvector <- c(1,2,3)
myvector2 <- scan()
1: 2
2: 1
#enter whenever need to stop
```
A vector can also can be join from another vectors:
```R
# Define two vectors
vector1 <- c(1, 2, 3)
vector2 <- c(4, 5, 6)

# Combine them into a single vector
combined_vector <- c(vector1, vector2)
```
We can perfome some kind of operartion in vectore but need to make sure that it all have the same lenght.
```R
# Define two vectors of the same length
a <- c(10, 20, 30)
b <- c(1, 2, 3)

# Perform element-wise addition
result <- a + b

# Print the result
print(result)
```
**Factor**\
A special kind of vector, contain unique values. Work the same way as set. \
**Matrice and arrays** \
Matrice: Vector but 2 demensions \
Arrays: Vetor but more than 3 demensions.
Declaring a matrix:
We can use matrix(declare a vector, number of rows, number of columns) function. \
Example:
```R
# Create a matrix with 3 rows and 2 columns
my_matrix <- matrix(c(1, 2, 3, 4, 5, 6), nrow = 3, ncol = 2)

# Print the matrix
print(my_matrix)

# This will return an NxN matrix that filled by the number in the c() function
my_matrix <- matrix(c(1, 2, 3, 4, 5, 6), nrow = 3)
```
Declaring a array:
```R
# Create a 3D array with dimensions 2x3x2
my_array <- array(1:12, dim = c(2, 3, 2))
# c(2,3,2) mean 2 rows, 3 columns, 2 layers

# Print the array
print(my_array)
```
**List**
A vector but can stored multiple type of value in 1 variable \
Declaring a list:
```r
#contain different types of data
myList<-list(5,6,"seven", mat)
```
**Data frame**
Think about it like a spreadsheet\
Declare a data frame
```r
# Create a data frame
my_data <- data.frame(
  name = c("Alice", "Bob", "Charlie"),
  age = c(25, 30, 22),
  passed = c(TRUE, FALSE, TRUE)
)

# Print the data frame
print(my_data)

# output
     name age passed
1   Alice  25   TRUE
2     Bob  30  FALSE
3 Charlie  22   TRUE
```
### Working with data object
**Vector** \
The index start from 1 \
The subvector can be retrive as:
```r
subvector <- my_vector[2:4]
```
A value of a vector can be override by
```r
myvector[index] <- new_value
```
Can use the sort() function to sort the element in vector\
Extract the data. We can extract the data by 2 ways
```R
#store index 2 and 3 of v1 intro v3
v3 <- v1[c(2,3)]
# can do it by logical extraction
v3 <- v1[v1>100] #store any number > 100 from v1 to v3
```
**Data frame**
As it is another variant of vector, we can use vector's trick with it.
```r
> x<-c(1,3,2,1)
> y<-c(2,3,4,1)
> xy<-data.frame(x,y) >xy
#output
  x y
1 1 2
2 3 3
3 2 4
4 1 1

> #use q to create new vector extracting x column of dataframe xy > q<-xy$x
>q<-xy$x
#output
[1]1 3 2 1
```
We can also add an additional row or colum into an existing data frame.
```r
# Add a new column 'z'
xy$z <- c(5, 6, 7, 8)
# Add a new row
new_row <- data.frame(x = 4, y = 5, z = 9)
xy <- rbind(xy, new_row)
```
**Checking and changing data type**
We can use the is."name of data type" function when we want to check if this variable is a that data type. \
We can use the as."name of data type" function when we want to convert this variable into a that data type.
```r
x <- 10
is.numeric(x)     # TRUE
is.character(x)   # FALSE

name <- "Alice"
is.character(name)  # TRUE
is.numeric(name)    # FALSE

flag <- TRUE
is.logical(flag)     # TRUE

# Convert numeric to character
x <- 42
x_char <- as.character(x)
is.character(x_char)  # TRUE

# Convert character to numeric
y <- "3.14"
y_num <- as.numeric(y)
is.numeric(y_num)     # TRUE

# Convert logical to numeric
flag <- TRUE
as.numeric(flag)      # Returns 1

#Example with data frame
df <- data.frame(name = c("Alice", "Bob"), age = c("23", "30"))

# Check type
is.character(df$age)   # TRUE

# Convert column to numeric
df$age <- as.numeric(df$age)
is.numeric(df$age)     # TRUE
```
**Missing value** \
Use NA. Treat it as null \
**Controll the work space** \
Use ls() or object() to list all the objects \
*Example*
```r
# Create some variables
x <- 10
y <- "hello"
z <- c(1, 2, 3)

# List all objects
ls()
#output
[1] "x" "y" "z"

object()
#output
[1] "x" "y" "z"
```
And use rm(object) for the removing part. \
*Example*
```r
# Remove one object
rm(x)

# Check again
ls()
# [1] "y" "z"
```