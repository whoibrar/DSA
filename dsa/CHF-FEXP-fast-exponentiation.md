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

- Charvee likes Mathematics. She wants to calculate a to the power b. Since the value may be very large so she is ok if she gets answer modulo 1e9+7. Help her calculate (a to the power b)%(1e9+7).

### Example

```

Input
- The first line of the input contains an integer T denoting the number of test cases. Next T lines contains the two numbers a and b.

Output
- Output the value in a new line.

Constraints
- 1<=T<=100
- 1<=a,b<=10^9

Input:
2
2 3
153536881 89094721

Output:
8
603732084

```

## Solution Approaches

### O(LogN) - Recursively Split in Half

- - Rewrite `x^n` recursively to find until `n==1 or n==0`
	- `x^n = x^(n/2) * x^(n/2)` if n is even 
	- `x^n = x^(n/2) * x^(n/2) * x` if n is odd 
- Applying Mod all over 

```cpp

#include <bits/stdc++.h>
using namespace std;

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

int main() {
	int t;
	cin >> t;
	while (t--) {

		long long int a, b;
		cin >> a >> b;
		cout << PowMod(a, b, 1e9 + 7) << endl;
	}

}


```

---

Return to [[DSA-Problems]]

---
