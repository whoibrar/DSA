---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/optimal-strategy-for-a-game-1587115620/1/#"
questionType : 

solvedDate : 2022-05-29 00:00:00 +0000
---

## Problem Statement

- You are given an array **A of size N**. The array contains integers and is of **even length**. The elements of the array represent N **coin** of **values V1, V2, ....Vn**. You play against an opponent in an **alternating** way.
- In each **turn**, a player selects either the **first or last coin** from the **row**, removes it from the row permanently, and **receives the value** of the coin.
- You need to determine the **maximum possible amount of money** you can win if you **go first**.

### Example

```

Input:
N = 4
A[] = {5,3,7,10}

Output: 15

Explanation: The user collects maximum
value as 15(10 + 5)

```

## Solution Approaches

### Understanding Game Mechanics

```cpp

// philosopy of approach: 
// 	1. Assume worst when things happen to you
//  2. Do best when you can

// when choosing amongst (a,b) players simply dont' grater of it
// but instead need to think a step further and choose something 
// that will bring the other one least profit(1)


// [Round] : [Player] : [Choice Available]
// [Player] -> [Chooses]

.
└── R1 : P1 : [ i ... j ]
    ├── P1 -> i
    │   └── R2 : P2 : [ i+1 ... j ]
    │       ├── P2 -> i+1
    │       │   └── R3 : P1 : [ i+2 ... j ]
    │       └── P2 -> j
    │           └── R3 : P1 : [ i+1 ... j-1 ]
    └── P1 -> j
        └── R2 : P2 : [ i ... j-1 ]
            ├── P2 -> i
            │   └── R3 : P1 : [ i-1 ... j-1 ]
            └── P2 -> j-1
                └── R3 : P1 : [ i ... j-2 ]



```

### Without DP

```cpp


long long solve(int arr[], int start, int end) {
	if (start > end) return 0;
	else if (start == end) return arr[start];

	int left = arr[start] + min(solve(arr, (start + 1)+1, end    ),
	                            solve(arr, (start + 1)  , end - 1));
	int right = arr[end] + min(solve(arr, start + 1, (end - 1)  ),
	                           solve(arr, start    , (end - 1)-1));
	return max(left, right);
}

```

### With DP O(N^2) sO(N^2)

```cpp

int DP[1000][1000];
long long solve(int arr[], int start, int end) {
	if (start > end) return 0;

	if (DP[start][end] != -1) {return DP[start][end];}
	int left = arr[start] + min(solve(arr, (start + 1) + 1, end),
	                            solve(arr, (start + 1)  , end - 1));
	int right = arr[end] + min(solve(arr, start + 1, (end - 1)  ),
	                           solve(arr, start, (end - 1) - 1));
	DP[start][end] = max(left, right);
	return DP[start][end];
}

long long maximumAmount(int arr[], int n) {
	memset(DP, -1, sizeof(DP));
	solve(arr, 0, n - 1);
}


```



---

Return to [[DSA-Problems]]

---