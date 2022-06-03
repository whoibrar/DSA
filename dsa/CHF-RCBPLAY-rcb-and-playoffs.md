---
published : false

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

- Team RCB has earned X points in the games it has played so far in this year's IPL. To qualify for the playoffs they must earn **at least** a total of Y points. They currently have Z games left, in each game they earn 2 points for a win, 1 point for a draw, and no points for a loss.
- Is it possible for RCB to qualify for the playoffs this year?

### Example

```

Input Format
- First line will contain T number of testcases. Then the testcases follow.
Each testcase contains of a single line of input, three integers X,Y,Z

Output Format
- For each test case, output in one line YES if it is possible for RCB to qualify for the playoffs, or NO if it is not possible to do so.
- Output is case insensitive, which means that "yes", "Yes", "YEs", "no", "nO" - all such strings will be acceptable.

 Sample Input 1

3
4 10 8
3 6 1 
4 8 2 

Sample Output 1

YES
NO
YES


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
		int x, y, z;
		cin >> x >> y >> z;
		if (x + (z * 2) >= y) {cout << "Yes" << endl;}
		else {cout << "No" << endl;}
	}

}

```

---

Return to [[DSA-Problems]]

---
