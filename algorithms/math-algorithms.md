### GCD algorithms

Hint: The gcd of two numbers will always be the less than or equal to the minimum of the two numbers.

-   **Brute force:** Basically check all numbers that divide the both numbers from 1 → (lower of the two numbers a,b). Then find the largest among the divisors that divide a,b. Worst-case complexity is O(min(a,b)) → O(n).
-   **Euclidean algorithm:** In this algorithm we exploit the idea that if a,b have a common factor 'f' then (a mod b) (which is a - k*b) also has the same common factor,
    - So a = n_{1} * f and b = n_{2} * f and f is the common factor of a, b.
    - So considering a mod b = a-k*b = (n_{1} - k*n_{2})*f. This means that a mod b also has same factor f.
    - _Theorem: gcd(a,b) = gcd(b,a mod b)_.
    - Using this our algo has two cases:
      * Base case: GCD (x,0) = x
      * Other case: GCD(a,b) = GCD(b, a mod b). This algorithm is a _tail linear recursive algorithm_
```Python
gcd(a,b):
# thumb rule try to keep larger value on the left
  if a < b:
     temp = a
     a = b
     b = temp
  if b == 0:
     return a
  return gcd(b, a % b)
# as this is tail recursive we can implement the same using a loop
```

### Checking if a number is prime or not

**The factors/divisors if they exist are always less then N(given number)**

- **Naive Method:** Here we would check all number before N if they divide it or n
    - Here we just check all numbers < n, which occurs in linearly.
    - Here the time complexity of the program is O(n)
```Python
isprime(n):
	i = 2
	while i < n:
      	      if n % i == 0:
      	      	 return False
	return True
```
- **Square-root method:** This method exploits the idea that the divisors/factors of a number are distributed around square root of n.
    - That is if a,b one of the pair of divisors where a*b = n, then it is observed that **a < square-root(n) < b** (if a < b and if b < a then interchange a, b)
      * Ex: 10, take 2,5 we know root(10) = 3.2 approx, So 2 < 3.2 < 5.
    - This square-root idea greatly reduces the number of divisors we need to check
    - The time complexity is O(square-root(n)) which is way less than above method.
```Python
isprime(n):
	i = 2
	while i**2 < n: # here we are checking i < square-root(n) basically
	      if n % i == 0:
	      	 return False
	return True
```