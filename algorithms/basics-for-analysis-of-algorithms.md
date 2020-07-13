---
title: "Basics for analysis of algorithms"
tags: ""
---
**Why Do we need to analyze algorithm?**

We need to analyze a particular algorithm because we need to understand the _resources_ that will be _needed_ to use the algorithm as our main objective is to develop an _efficient algorithm_

## Performance analysis of algorithm

-   Apriori analysis: This is the analysis of the algorithm before it is implemented.	space complexity ← _apriori analysis_ → time complexity.
-   Aposteriori analysis: This is the analysis done when the algorithm is implemented, so the actual values of the program are analyzed here.

## Apriori Analysis

### Time Complexity

The total amount of time required by the algorithm to complete the task. In  simple, **total time needed** to run the algo.

**Q)** Ok, now we said that it is the total time req. so now how do we actually calculate the time? On what basis do we calculate it?

#### Concise explanation of different worst-case times (Big(O))

![different Notations](https://www.geeksforgeeks.org/wp-content/uploads/mypic.png)

### Space complexity

The total amount of space required by the algorithm to complete the task. In simple, **total memory needed** to run the algo.

**Q)** Ok, now we said that it is the total memory req. so now how do we actually calculate the memory? On what basis do we calculate it?

We calculate the total memory so now for calculating that we need to understand the types of memory:

-   Fixed memory ( this is independent of _input and output characteristics_ :-  size and number of values)
-   Variable memory

#### Fixed memory

This is classification of memory used that are either:

-   Space for code (assuming implementation)
-   Simple variables
-   Constants
-   Component variables (variables that contain additional inner components like structures in C or classes in Java)
