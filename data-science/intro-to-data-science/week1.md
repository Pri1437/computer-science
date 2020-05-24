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
* We can concatenate lists by using +, Ex: ['a','b','c'] + [1,2,3] &rarr; ['a','b','c',1,2,3] (no nested lists present)
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
For handling data and time we use **datetime and time** libraries

There are many methods to store date and time, one of the method is to store date and time in seconds (legacy method)

time.time() &rarr; returns time in seconds relative to jan 1, 1970 (epoch)

Timestamp &rarr; record of data and time of an event that has occurred.
* To create a timestamp in python we use datetime library
* datetime.datetime.fromtimestamp(time in seconds relative to epoch) &rarr; returns an **date-time object** consisting of date, time based on seconds mentioned.
* Ex: datetime.datetime.fromtimestamp(time.time()) &rarr; gives the datetime object consisting of current date and time.

We can do arithmetic on time and date by the use of **time deltas**.
* datetime.timedelta(days=100) &rarr; create timedelta of 100 days.

datetime.date.today() &rarr; returns current local date

We can add/subtract date value with time delta to get required date.

#### Ojects and map() in Python
Python supports objects and classes.
* "class" keyword used for class creation
* 'doc string' &rarr; tells about a class, it is just for readability
    - "doc_string" (basically a string which is not assigned to any variable)
    - To read doc string of an object call "obj_name.__doc__"
    
* **Everything in python is an object**.
    - The variables used are just references.
    - So a=2 and b=2, suggests us that a and b are pointing to the same object "2". (similar to Java) This allows in efficient use of memory.
    - In contrast to the implementation in C, where each memory is linked to a name and so a, b would be different memory locations hold value 2.
    - So any object can be linked to a name, hence the concept of dynamic typing.
    - Functions are objects too, so they can be identified with a name. Ex: a = addNum

* **Namespaces:**
      * These are collection of names that are mapped to objects
      * Three main type of name spaces &rarr; inbuilt namespaces(present until the interpreter is running), module(global), function(local).
      * Different namespaces can co-exist together and are isolated
      * As namespaces are isolated names can be reused.
      * We can use the concept of scoping as a direct result of namespaces.

* **Scoping:**
      * scope in function, scope in module(program), scope in inbuilt names
      * First local namespace is searched, then global, then inbuilt namespace.
      * "global" keyword is used to convert a local namespace name to global namespace name. (wherever "global" keyword is used that name is linked to the global namespace and not the other names that are same which are present in different local namespace)
```Python
a=5
def num():
    a=2
    print(id(a),a) # output for 2
print(id(a),a) # output for 5

def look():
    global a #makes local a into global, so all changes made reflect to the global a
    a=3
    print(id(a),a) #output for 3
print(id(a),a) #output for 3 again!
```
* Classes:
    - In python, every **class definition** creates a class object by default by the **name of the class**. This class object is used to create other objects of the class.
      * This object implicitly created by the class name is of no use to us but just to create instants of class.
      * Functions in classes are function objects.
      * "self" parameter &rarr; refers to the instance of the class that calls an instance method. (we use self just by convention)
* Objects:
    - Created using class object.
    - "objName=className()"
    - Functions in objects are method objects
    -Actually when we call a method of object, the respective is passed into the method implicitly. (So by default every method in class should have atleast one parameter)
    - "object.method()" is other way of writing "class.method(object)"

Coming to map() in python
* map() is used for applying a certain function on a iterable object which can be list, tuple, dictionary etc.
* Basically acts like a transformation.
* map(function, parameter), parameter &rarr; iterable object. Number of parameters present in map depends on number of parameters that can be taken by the function.

#### Lambda and list comprehensions
* Lambda functions &rarr; anonymous function, can only take one sentence as function body.
* Lambda functions are of great use for cleaning of data.
* "lambda parameters: what to return(in single line)"
* List comprehensions are to input list using generating expressions(which can use conditional statements)
* List comprehensions basically make inputing particular values in lists easy and in a compact manner.
* listName = [var for i in sequence: conditions on var]

#### Numerical Python library (NumPy)
