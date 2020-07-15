---
title: "Basics for analysis of algorithms"
tags: ""
---
**Why Do we need to analyze algorithm?**

We need to analyze a particular algorithm because we need to understand the _resources_ that will be _needed_ to use the algorithm as our main objective is to develop an _efficient algorithm_

## Performance analysis of algorithm

-   Apriori analysis: This is the analysis of the algorithm before it is implemented.	space complexity ← _apriori analysis_ → time complexity.
-   Aposteriori analysis: This is the analysis done when the algorithm is implemented, so the actual values of the program are analyzed here.

## Apriori Analysis (analysis without actually running the code)

### Time Complexity

The total amount of time required by the algorithm to complete the task. In  simple, **total time needed** to run the algo.

So in general we consider **1 unit of time** as any basic operations like assignment, arithmetic, condition checking.

We use unit of time (rather than seconds) to basically standardize and to calculate the performance of any algorithm independent of machine specifications.

To assess performance we mainly look at relation between **input size and time taken**. Here also we try to understand the **approximate growth of time rather than exact value**

To explain the upper bound (worst-case), lower bound (best-case), tight bound (average-case) we use asymtotic notations:
* In most cases, we generally try to calculate worst-case
* big O notation is used for worst-case
* big Omega notation is used for best-case
* big Theta notation is used for average-case

**We try to consider the upper, lower and tight bound functions as close to our actual function for time to be understand the nature of growth more accurately.**

**Acutally finding out the upper, lower and tight bound**, let f(n) be our function:
* O(g(n)) &arr; a > 0, c > 0 (constant) such that for some c and for all n > a, f(n) <= c*g(n) then we say f(n) is O(g(n)) which means **g(n) is upper bound of f(n)**

![big Oh](https://cdn.programiz.com/sites/tutorial2program/files/big0.png)
* Omega(g(n)) &rarr; a > 0, c > 0 (constant) such that for some c and for all n > a, f(n) >= c*g(n) then we say f(n) is Omega(g(n)) which means **g(n) is lower bound of f(n)**

![big omega](https://cdn.programiz.com/sites/tutorial2program/files/omega.png)
* Theta(g(n)) &rarr; a > 0, c1 > 0 and c2 > 0 (constants) such that for some c1, c2 and for all n > a, c1*g(n) <= f(n) <= c2*g(n) then we say f(n) is Theta(g(n)) which means **g(n) is tight bound of f(n)**
     - When O(g(n)) = Omega(g(n)) then Theta(g(n)) is true
     - When Theta(g(n)) implies O(g(n)) and Omega(g(n))

![big theta](https://cdn.programiz.com/sites/tutorial2program/files/theta.png)

#### Thumb rules for finding time functions and their asymptotic notations
* Drop lower terms in cas of polynomials, as we deal with large inputs we have to only take the largest power
* Drop off coeff. / constant multipliers (as this is taken care in definations)
* In case of different functions like f(n) = 5n + log(n) only consider that part which **grows fastest** for n &rarr; infinity
    - So here 5n > log(n), as n &rarr; infinity so f(n) is O(n).
* In case of conditional statements, we don't add times of the different parts we only consider the branch that leads to block that takes most time to execute.
* In case of **recursion**, either make a **recurrence relation or try to create recursion tree**.
    - Recursion tree &rarr; tells about how many times the function is being called, so total number of calls multiplied by average time taken for each call is total time.
* Generally part of code that takes maximum time controls the overal time complexity of the program.

#### Concise explanation of different worst-case times (Big(O)) (growth of diff functions)

![different Notations](https://www.geeksforgeeks.org/wp-content/uploads/mypic.png)

### Space complexity

The total amount of space required by the algorithm to complete the task. In simple, **total memory needed** to run the algo.

**Q)** Ok, now we said that it is the total memory req. so now how do we actually calculate the memory? On what basis do we calculate it?

We calculate the total memory so now for calculating that we need to understand the types of memory:

-   Fixed memory ( this is independent of _input and output characteristics_ :-  size and number of values)
    - We take them as constants.
-   Variable memory &rarr; memory that changes either due to recursion, collections, arrays etc.

#### Fixed memory

This is classification of memory used that are either:

-   Space for code (assuming implementation)
-   Simple variables
-   Constants
-   Component variables (variables that contain additional inner components like structures in C or classes in Java)

Just like time complexity we calculate space complexity where each variable created is considered as 1 unit of memory.

We try to understand how memory is consumed based on size of input.

For recursion, generally try to make recursion tree and calculate number of function calls, as space complexity is proportional to calls.

Like in time complexity we have same asymptotic notation and we consider the higher order terms as here too we assume input size is large (asymptotic)

Generally space complexity is governed by the part of code that takes up maximum memory.
