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

solvedDate : 2022-05-26 00:00:00 +0000
---

## Problem Statement

- Given a positive number N, you have to find if N is a Harshad number or not.  
A number N is called a "Harshad number" if and only if NmodK=0, where K denotes the sum of digits of N. That is, N should be divisible by the sum of its digits.

### Example

```
Input
- The first line of the input contains a single integer T denoting the number of test cases. The description of T test cases follows.
- The first and only line of each test case contains one integer N

Output
- For each test case, print a single line containing "Yes" or "No".

Example Input

5
10
13
75
55640877376
3622056459435540

Example Output

Yes
No
No
Yes
Yes

```

## Solution Approaches

### O(N) - Using Simple Counter 

```cpp

#include <bits/stdc++.h>
using namespace std;


int main() {
	int t;
	cin >> t;
	while (t--) {
		long long int n;
		cin >> n;
		long long int copy = n;
		int k = 0;
		while (n > 0) {
			k += n % 10;
			n = n / 10;
		}

		if (copy % k == 0) {cout << "Yes" << endl;}
		else {cout << "No" << endl;}
	}

}


```

---

Return to [[DSA-Problems]]

---
