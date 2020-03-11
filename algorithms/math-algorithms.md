---
title: "Math algorithms"
tags: ""
---
### GCD algorithms

Hint: The gcd of two numbers will always be the less than or equal to the minimum of the two numbers.

-   **Brute force:** Basically check all numbers that divide the both numbers from 1 → (lower of the two numbers a,b). Then find the largest among the divisors that divide a,b. Worst-case complexity is O(min(a,b)) → O(n).
-   **Euclidean algorithm:** In this algorithm we exploit the idea that if a,b have a common factor 'f' then (a mod b) (which is $a - k \\times b$) also has the same common factor,
    $\\$ So $a=n_{1} \\times f$ and $b=n_{2} \\times f$ and $f$ is the common factor of a, b. $\\$
    So considering a mod b = $a-k\\times b$ = $(n_{1} - k \\times n_{2})\\times f$. This means that a mod b also has same factor $f$.
    _Theorem: $gcd(a,b)=gcd(b,a\\mod b)$_. $\\$
    Using this our algo has two cases:$\\$
    Base case: GCD (x,0) = x $\\
    $Other case: GCD(a,b) = GCD(b, a mod b). This algorithm is a _tail linear recursive algorithm_
