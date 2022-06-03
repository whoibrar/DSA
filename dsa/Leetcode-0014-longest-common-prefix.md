---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://leetcode.com/problems/longest-common-prefix/"
questionType : 

solvedDate : 2022-05-31 00:00:00 +0000
---

## Problem Statement

- Write a function to find the longest common prefix string amongst an array of strings.
- If there is no common prefix, return an empty string `""`.

- Same as [Longest Common Prefix in an Array - Practice - GeeksforGeeks](https://practice.geeksforgeeks.org/problems/longest-common-prefix-in-an-array5129/1)

### Example

```

Input: strs = ["flower","flow","flight"]

Output: "fl"

```

## Solution Approaches

### O(N * LogN) Sort to Compare first and last

- Sort the given array
	- Last element will be `mismatced` characters to end, if any
	- otherwise its sorted based on alphabetical order
- The longest common prefix shall in both first and last, so we need to iterate and compare for every character through these two.

```python

def longestCommonPrefix(self, strs: List[str]) -> str:
	strs.sort()
	first,last = strs[0],strs[-1]
	i=0
	while(i < (min(len(first),len(last)))):
		if(first[i]!=last[i]):
			break
		i+=1
	return first[:i]

```

- Submitted to [Longest Common Prefix in an Array - Practice - GeeksforGeeks](https://practice.geeksforgeeks.org/problems/longest-common-prefix-in-an-array5129/1)

```cpp

string longestCommonPrefix (string arr[], int N)
{
	sort(arr, arr + N);
	string first = arr[0];
	string last = arr[N - 1];
	int i = 0;
	// cout << first.size();
	while (i < min(first.size(), last.size())) {
		if (first[i] != last[i]) {
			break;
		}
		i++;
	}
	if (i == 0) return "-1";
	return first.substr(0, i);
}

```

---

Return to [[DSA-Problems]]

---
