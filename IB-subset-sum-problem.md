---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://www.interviewbit.com/problems/subset-sum-problem/"
questionType : 

solvedDate : 2022-05-29 00:00:00 +0000
---

## Problem Statement

- Given an integer array **A** of size **N**.
- You are also given an integer **B**, you need to find whether their exist a subset in **A** whose sum equal **B**.
- If there exist a subset then return **1** else return **0**.

- Same as [Subset Sum Problem - GeeksforGeeks](https://practice.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1/#)

### Example

```

Input:
 A = [3, 34, 4, 12, 5, 2]
 B = 9

Output: 1 

Explanation: Here there exists a subset with
sum = 9, 4+3+2 = 9.

```

## Solution Approaches

### Vanilla Recursion 

- Since we are asked to check if we can form a subset who's sum is equal to `sum`, for every element of array there can only be two possibilities, `take` or `pass`. 
	- `take` : considering current element to be part of subset, then remaining required sum will be `sum-arr[curr]`
	- `pass` : contrary to above, since we don't consider it, value of sum remains unchanged as `sum`
- Whether we take or pass we will have to move to next element, `curr+1`
- Reaching `sum==0` happens in recursive call when we have collected `taken` all the required elements to form subset. This signifies success.
- `curr>v.size()` reaching past the end of given array.


```cpp

bool solve(vector<int>v, int sum, int start) {
	if (sum == 0) {return true;}
	if (start > v.size()) {return false;}

	bool take = solve(v, sum - v[start], start + 1);
	bool dont = solve(v, sum, start + 1);

	return (take or dont);
}

bool isSubsetSum(vector<int>arr, int sum) {
	return solve(arr, sum, 0);
}

```

### O(N * Sum) - DP to above

```cpp

int DP[101][100001];

bool solve2(vector<int>v, int sum, int curr) {
	if (sum == 0) {return true;}
	if (curr > v.size()) {return false;}

	if (DP[curr][sum] != -1) {return DP[curr][sum];}
	else {
		bool take = solve(v, sum - v[curr], curr + 1);
		bool pass = solve(v, sum, curr + 1);

		DP[curr][sum] = (take or pass);
		return DP[curr][sum];
	}
}

bool isSubsetSum(vector<int>arr, int sum) {
	memset(DP, -1, sizeof(DP));
	return solve2(arr, sum, 0);
}

```

---

Return to [[DSA-Problems]]

---
