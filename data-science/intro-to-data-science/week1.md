## Introduction to Data science
Some useful points about python:
* General purpose language
* Has a specific ecosystem for data science known as **SciPy**
* The SciPy stack contains libraries like pandas and matplotlib
* Pandas &rarr; data querying and manipulating of data
   - Pandas uses relation theory similar to DBMS
* Matplotlib &rarr; plotting using data

Q) What do you think of data science?
Ans) Basically study of data and various aspects of data.

Q) Why is there a lot of demand for data scientist?
Ans) It is basic to create any product we need data about the interests of customers, their needs / requirements etc. So to better understand this data, how to interpret this data we need data scientist.

Data science Consists of:
* Hacking skills
* Math and statistics knowledge
* Substantive expertise
* Skepticism
* experimentation, simulation and replication

A data scientist should be able to convey communicate the their findings that can include graphs, charts etc.

Data science can be summed up as (quoted by Donoho)
* Exploration and preparation of data (extracting and cleaning of data)
* Structuring, representing and transforming data (i.e. converting it into useful stuff)
* Computing the data from previous stages
* Data modeling &rarr; predictive, generative modeling
* Data visualization and presentation &rarr; using graphs, charts, 3d models to visualize the results
* Science in data science &rarr; exploring/discovering different techniques and methods that work for data science.

Data science kinda marries statistics and machine learning together.

## Basics of python programming language
### New stuff learnt about functions

By giving a value to a parameter before calling the function is basically considering that value to be a default value in case we don't give a value to that parameter during the call.

If value is specified then value passed on is considered.
**But if the value is not mentioned then it is bound that function has to be called with that many parameters.**
```Python
def add_numbers(x,y,z=None): #None is a keyword for no value and here a default val
     if(z==none):
	return x+y
     else:
	return x+y+z

#calling function without mentioning z value
print(add_numbers(2,2))

#calling function mentioning z value
print(add_numbers(1,2,3)) # after function is called z=3 not "None"
```
The optional parameters come at the end of function declaration

Multiple "if"s are evaluated simultaneous whether others pass or fail and "if" with "elif" just evaluates the other if the first one fails

We can assign a function to a variable
```Python
def add_numbers(x,y)
    return x+y

a = add_numbers # assigns function to "a" which can be used as the function name
a(1,2) #like add_numbers(1,2)
```

### Types and sequences in Python
**type(object)** &rarr; to return type of object
* Can tell function, int, float, NoneType etc.

#### Tuple
**Tuples** are a type of data structure that are **immutable**
* Can't change the inner values but the var can be reassigned with another

#### List
**Lists** are type of data structure that are **mutable**
* We can concatenate lists by using +
* If we want to repeat elements in list by some amount we use *, **(list)\*num** and it gets repeated "num" times.
* use "in" operator to check something in list. ex val in list
* -ve indexes allowed &rarr; start from end "-1" being last element.

#### Strings
Slicing a **string** using bracket notation:
* str[starting : ending] &rarr; gets all those chars from starting index to ending(ending index is excluded).
    - Ex: str[4:5] &rarr; get chars from 4th index to 4th index(5-1).
    - **if starting = ending &rarr; doesn't get any value**
    - **str[i:] &rarr; means from "i" to end of string.**
    - **str[:k]** &rarr; means start from beginning and end just before kth index
* If we are trying to get anything out of bound then it doesn't get anything.
* Occurs in "left to right" fashion.

String allow use of -ve indexes used to start from end, "-1" being index of last element.

Slicing with -ve indices is allowed &rarr; str[-i:-j] means start from ith index from end and stop just before jth index from end.

We can use "in" operator to check a substring, "*" for repeating string "num" times and "+" for concatenating two strings.

string.split(delimiter) &rarr; splits a string into "class List"(list)
* string.split(delimiter)[i] &rarr; first splitting and then getting the ith index element from the list created.

In python, we have dedicated functions that are used for type-casting.

Formatting strings:
* Use of **string.format()** functions, generally while outputing only
* {} &rarr; format specifiers, basically blanks in string to put certain values
* format just replaces {} with the corresponding values temporarily, so doesn't actually change the original string
    - So to be able to store this new string we can assign is to another var.
```Python
str='{} is a good {}'
print(str.format('pri','boy')

# output: pri is a good boy
```
String formatting is important in manipulation and data cleaning

#### Dictionaries
**Dictionaries** are data structure in python that use **key-value pairs**.
* {key:value, key:value, ...} &rarr; dictionary.
* keys are used to identify values they are mapped/paired with.
* keys &rarr; be int, float, string but not an collection data structure
* **Each key is unique**
    - Ex: {2:1, 2:2} &rarr; here key value 2 will only be paired with latest value that is 2. (just the value is reassigned)
* values &rarr; can be anything
* No ordering in dictionary

Iterating over keys "for i in x" x is dictionary, i will take values of keys.(we could use **x.keys()** also)

Iterating over values "for i in x.values()" where x.values() returns all the dictionary values.

Iterating over all of items (key-value pairs) "for key,value in x.items", x.items returns key, value (same order).

We can give values of a sequence to multiple variables but **number of vars = number of elements in sequence**.

Difference b/w OrderedDict() and dict():
* Initialization:
    - OrderedDict() function is used to tell
    - {} for normal dictionary
* normal dictionary doesn't remember the order of insertion of elements while Ordered dictionary does.
* To be able to use ordered dictionary we need to import it from **collections package**.

#### Reading and Writing CSV files
CSV &rarr; .csv files

To work on csv files we **import csv package**

**Slicing is allowed in any collection by use of : in [].**

We can use **csv.DictReader(csvfile)** to read the csv file and stores them as ordered dictionary.
* We store each row of the csv file as ordered dictionary and all the rows together as a list.

%precision 2 &rarr; for controlling the decimal places for floating points while printing (used only in IPython).

"With" keyword &rarr; used to reduce lines of code when dealing with exception handling like file streams.
```Python
with open('file.csv', 'w') as file: #basically the file is used to handle file.csv
     file.write('Hello there!')
```
"as" keyword is to create an alias of something that can be module, function etc.

"sum(iterable, start)" it is an inbuilt function that calculates sum of numbers in list.
* Returns sum of start and elements of the iterable.
* **start** (optional) &rarr; the values in the iterable are added to this value.
* Can use generating expressions as iterables.

"'str'.join(sequence)" will return a string that place 'str' in between every consequtive elements of the sequence. Ex: 'hi'.join(['hello','bye','ohh']) &rarr; 'hellohibyehiohh'

**Generator expression** &rarr; d for d in sequence, as it is generating val 'd' using sequence.

**set(iterable)** &rarr; creates a Python set of elements from an iterable.
* Python set &rarr; use {elements}
    - Ex: {1,2,3}
    - But x = {} &rarr; creates an empty dictionary not an empty set
* Inbuilt function.
* Iterable &rarr; list, tuple, generating expression, string.
* returns empty set when no parameters

#### Dates and times in Python
time.time() &rarr; returns time in seconds relative to jan 1,1970 (epoch)

