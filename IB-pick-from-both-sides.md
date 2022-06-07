---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://www.interviewbit.com/problems/pick-from-both-sides/"
questionType : 

solvedDate : 2022-06-03 00:00:00 +0000
---

## Problem Statement

- Given an integer array A of size N.
- You have to pick exactly B elements from either left or right end of the array A to get maximum sum.
- Find and return this maximum possible sum.

### Example

```

Input 1:
 A = [5, -2, 3 , 1, 2]
 B = 3
Output 1:
 8
Explanation 1:
Pick element 5 from front and element (1, 2) from back so we get 5 + 1 + 2 = 8
 
Input 2:
 A = [1, 2]
 B = 1
Output 2:
 2
Explanation 2:
 Pick element 2 from end as this is the maximum we can get


```

## Solution Approaches

### Recursively Solving 

- Similar to [[GFG-optimal-strategy-for-a-game]]
	- But there is only single player, so no need to use `min` part
	- Recursive tree is drawn only till `k-th` depth
	- Values of sum at leaf nodes at this depth will contain ans.

```cpp

int ans = 0;
void rec(vector<int> &a, int k, int start, int end, int sum, int picked) {
	if (start > end) return;
	else if (picked == k) {
		ans = max(ans, sum);
		return;
	}
	else {
		rec(a, k, start + 1, end, sum + a[start], picked + 1);
		rec(a, k, start, end - 1, sum + a[end], picked + 1);
	}

}

int pickfromsides(vector<int> &a, int k) {
	rec(a, k, 0, a.size() - 1, 0, 0);
	return ans;
}


```


---

Return to [[DSA-Problems]]

---
