---
title: "Recursion"
tags: ""
---
There are many types of recursion:

1) Linear recursion: Here the function calls itself once in a statement where it is called.

```C
double my_sqrt(double x, double a)
{
	double difference = a*x-x;
	if (difference < 0.0) difference = -difference;
	if (difference < EPSILON) return(a);
	else return(my_sqrt(x,(a+x/a)/2.0)); // here the function is called once
}
```

_Tail recursion_: It is a type of linear recursion where the function call is the final statement of the function body. 

Generally, Tail recursion → iteration, by replacing the function call with a loop.

```C
int gcd(int m, int n)
{ 
	int r; 
	
	if (m < n) return gcd(n,m);

	r = m%n;
	if (r == 0) return(n);
	else return(gcd(n,r));
}
```

2) Binary recursion: Here the function is called twice in the same calling statement. The mathematical combinations operation is a good example of a function that can quickly be implemented as a binary recursive function. 

```C
int choose(int n, int k)
{
	if (k == 0 || n == k) return(1);
	else return(choose(n-1,k) + choose(n-1,k-1));
}
```

3) Non-linear recursion: Here the function is called more than two times in the calling statement.

4) Mutual recursion: Here one function calls another function and that calls another and the final one calls the first function. For example, function A calls function B which calls function C which in turn calls function A.

```C
int odd(int number){
	if (number==0) 
		return 0;
	else
		return even(number-1);
}

// returns 0 if the given number becomes 0, so the given number is even
// returns odd(number - 1) elsewhere
int even(int number){
	if(number==0) 
		return 1;
	else
		return odd(number-1);
}
```
