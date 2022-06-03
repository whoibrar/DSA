---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : 
questionType : 

solvedDate : 2022-05-27 00:00:00 +0000
---

## Problem Statement

- Implement pow(x, n) % M.  
- In other words, given x, n and M, find (xn) % M.

### Example

```

Input:
x = 2, n = 6, m = 10

Output:
4

Explanation:
26 = 64
64 % 10 = 4


```

## Solution Approaches

### O(LogN) Recursively Split in Half 

- Same as [[CHF-FEXP-fast-exponentiation]]

```cpp

// x^n % m

long long int PowMod(long long int x, long long int n, long long int M) {
	int sign = 1;

	if (n < 0) {sign = -1; n = n * sign;}
	else if (n == 0) {return 1;}
	else if (n == 1) {return x % M;}

	long long int ans = PowMod(x, n / 2, M); ans = ((ans % M) * (ans % M)) % M;
	if ((n & 1) == 1) {ans *= (x % M);}

	return (ans * sign) % M;
}

```
---

Return to [[DSA-Problems]]

---
