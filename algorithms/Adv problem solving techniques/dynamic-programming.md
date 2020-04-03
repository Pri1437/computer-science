---
title: "Dynamic programming"
tags: ""
---
_Cormen: Chapter 15_$\\$
When developing an algorithm we consider a set of choices (steps), in each step we face some subproblem(s).

A prob. may have multiple sol. Every sol. has a val (cost), optimal solutions are sol. with min/max val.

There is always a possibility that subproblems repeat.

Q) What is Dynamic programming?

-   DP → technique that stores solutions of subproblems that may repeat.
    -   Like making notes and going through them instead of reading the chapter again when a doubt arises.
-   problem → divided into subproblems then solutions of subproblems are combined
-   _tabular method to solve_

Q) Why to use it and when to use it?

-   DP solves a subsubprob only once and stores its value in a table
    -   same problem is not computed again
-   DP is useful when you have subproblems repeat in atleast two or more steps in algo.

DP vs Divide and conquer:

-   DP needs the subproblems to _overlap_
-   Divide and conquer require subproblems to be _disjoint_

Steps followed when DP algo is made:

-   Describe the structure of optimal sol.
-   By a recursive sol describe cost of optimal solution.
-   Compute the cost of optimal solution
-   Construct the optimal solution from the info.

### Rod cutting problem

Here we cut a rod into smaller lengths to maximize the total value.$\\$
Assumptions:

-   Table consisting of prices of different rods $p_i$
-   Integral lengths 'i'
-   Cost of cutting is free

Objective: To get _maximum profit_ by selling a rod, either by cutting it or not.

As the cutting and not cutting the rod at a given length 'i' from the left side are independent choices, so total _number of combinations of cuts $2^{n-1}$_ where 'n' is the length of the original rod.

Max revenue of 'n' $r_n$ = max ($p_n, r_1 + r_{n-1}, r_2 + r_{n-2} ..., r_{n-1} + r_1$) , $p_n$ → price of uncut rod $\\$
The pairs 'i' and 'n-i' which can be cut further have optimal revenues $r_i$ and $r_{n-i}$ where i = 1, 2, 3, ..., n - 1. 

-   Here we view decomposition of rod as two new subproblems.

Since we don't know which value of 'i' gives optimal revenue, we will have to check all the possible cases.	So the problem will have optimal solution if the subproblems are having optimal solution too! (_optimal substructure_).

We can view the decomposition in a different way,

-   The left end we keep it aside and only the right end is further allowed to be divided.
    -   This way we reduce to one subproblem
    -   So now the $r_i$ (left end) = $p_i$ and $r_{n-i}$ is optimal revenue of 'n-i' length rod.
    -   we consider $r_0=0, \\therefore$  $r_n$ = $\\max_{1\\leq i \\leq n} (p_i + r_{n-i})$ is the new modified equation.

The implementation of the above eq returns max revenue possible for n,

```C
cut-rod(p[], n) // p[] array of prices, n is length of rod
{
    if(n==0) // length of rod = 0
        return 0;
    q=-infinity; // max revenue
    for(i=1;i<=n;i++) // to check all the cutting ,combination
    {
        q=max(q, p[i] + cut-rod(p, n-i) );
    }
    return q;
}
```

-   The time complexity of this implementation is very large as 'n' ↑ which is in exponential order.
    -   This is not surprising because total number of combinations that we need to check is $2^{n-1}$.
    -
    -   This is because this algo calls itself recursively and computes the same parameters (subproblems) over and over.
    -   You can use recursive trees for writing recurrence relations.

* * *

### Matrix-chain multiplication problem

Multiplying matrices while performing lowest scalar multiplication$\\$

* * *

### Elements of dynamic programming

Conditions that optimization problems need to make DP a viable solution.$\\$

* * *

### Longest common subsequence problem

Finding longest common subsequence from two sequences.$\\$
**Subsequence:** It is a new sequence which is created by deleting some or no elements from original sequence.

* * *

### Optimal binary search trees

Constructing BST by using DP
