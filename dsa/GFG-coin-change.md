---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/coin-change2448/1#"
questionType : 

solvedDate : 2022-05-30 00:00:00 +0000
---

## Problem Statement

- Given a value N, find the number of ways to make change for N cents, if we have infinite supply of each of S = { S1, S2, .. , SM } valued coins.

### Example

```

Input:
n = 4 , m = 3
S[] = {1,2,3}

Output: 4

Explanation: Four Possible ways are:
{1,1,1,1},{1,1,2},{2,2},{1,3}.

```

## Solution Approaches

### Recursion Only

```cpp

// repetation of recursion calls allowed
////////////////////////////////////////

int solve(int coins[], int n, int amount) {
	if (amount == 0) {return 1;}
	else if (amount <= 0) {return 0;}

	int ways = 0;

	for (int i = 0; i < n; i++) {
		ways += solve(coins, n, amount - coins[i]);
	}
	return ways;
}

int main() {
	int arr[] = {1, 2};
	cout << solve(arr, 2, 4);

}

// repetation of recursive calls  not allowed
/////////////////////////////////////////////

int solve(int coins[], int n, int amount, int current) {
	if (amount == 0) {return 1;}
	else if (amount <= 0) {return 0;}

	int ways = 0;

	for (int i = current; i < n; i++) {
		ways += solve(coins, n, amount - coins[i], i);
	}
	return ways;
}

int main() {
	int arr[] = {1, 2, 3};
	cout << solve(arr, 3, 6, 0);

}
```

### Recursion With DP

```cpp

int DP[1001][1001];

int solve(int coins[], int m, int amount, int current) {
	if (amount == 0) return 1;
	if (amount < 0 || current > m ) return 0;

	if (DP[amount][current] == -1) {
		int take = solve(coins, m, amount - coins[current], current);
		int next = solve(coins, m, amount, current + 1);
		DP[amount][current] = take + next;
	}
	return DP[amount][current];

}

long long int count(int S[], int m, int n) {
	memset(DP, -1, sizeof(DP));
	return solve(S, m - 1, n, 0);
}


```



---

Return to [[DSA-Problems]]

---