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

- Chef has an exam which will start exactly M minutes from now. However, instead of preparing for his exam, Chef started watching Season-1 of Superchef. Season-1 has N episodes, and the duration of **each** episode is K minutes.
- Will Chef be able to finish watching Season-1 **strictly before** the exam starts?

### Example

```

Input Format
- The first line contains an integer T denoting the number of test cases. T test cases then follow. The first and only line of each test case contains 3 space separated integers M, N and K

Output Format
- For each test case, output on one line YES if it is possible to finish Season-1 strictly before the exam starts, or NO if it is not possible to do so.
- Output is case insensitive, which means that "yes", "Yes", "YEs", "no", "nO" - all such strings will be acceptable.

Sample Input 1

3
10 1 10
25 2 10
15 2 10

Sample Output 1

NO
YES
NO

```

## Solution Approaches

### O(1) - Direct Formula

```cpp

#include <bits/stdc++.h>
using namespace std;


int main() {
	int t;
	cin >> t;
	while (t--) {
		int m, n, k;
		cin >> m >> n >> k;
		if (n * k < m) {cout << "Yes" << endl;}
		else {cout << "No" << endl;}
	}

}


```

---

Return to [[DSA-Problems]]

---
