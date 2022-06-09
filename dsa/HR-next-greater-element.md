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

solvedDate : 2022-06-09 12:37:59 +0530


created_at: 2022-06-09 12:39:54 +0530
modified_at: 2022-06-09 19:04:56 +0530
---

## Problem Statement

- Given an array, print the Next Greater Element (NGE) for every element. The Next greater Element for an element x is the first greater element on the right side of x in array. Elements for which no greater element exist, consider next greater element as -1.

### Example

```
For the input array [4, 5, 2, 25}, the next greater elements for each element are as follows.
Element --> NGE
4 --> 5
5 --> 25
2 --> 25
25 --> -1


```

## Meta Data

### Link 

- [Next Greater Element - HackerRank](https://www.hackerrank.com/contests/second/challenges/next-greater-element/problem)

### Tags 

- [[Stacks]]

### Similar 

- [[Leetcode-0496-next-greater-element-i]]

## Solution Approaches

### O( N ) Using Stacks

- Maintain a stack of elements until now, if the current element is greater than the stack elements assign to that value.
- Initialize with `-1` so to checking at the end 

```cpp

#include <bits/stdc++.h>
using namespace std;

vector<int> nge(vector<int> &v) {
	vector<int> ans(v.size(), -1);
	stack<int> st;
	for (int i = 0; i < v.size(); i++) {
		while (!st.empty() and v[i] > v[st.top()]) {
			ans[st.top()] = v[i];
			st.pop();
		}
		st.push(i);
	}
	return ans;
}

int main() {
	int n; cin >> n;
	vector<int> v;
	for (int i = 0; i < n; i++) {
		int temp; cin >> temp;
		v.push_back(temp);
	}
	auto ans = nge(v);
	for (int i = 0; i < n; i++) {
		cout << v[i] << " " << (ans[i] == -1 ? -1 : ans[i]) << endl;
	}
}


```


---

Return to [[DSA-Problems]]

---
