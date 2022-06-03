---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://leetcode.com/problems/find-first-palindromic-string-in-the-array/"
questionType : 

solvedDate : 2022-05-17 00:00:00 +0000
---

## Problem Statement

- Given an array of strings `words`, return _the first **palindromic** string in the array_. If there is no such string, return _an **empty string**_ `""`.

### Example

```

Input: words = ["abc","car","ada","racecar","cool"]
Output: "ada"
Explanation: The first string that is palindromic is "ada".
Note that "racecar" is also palindromic, but it is not the first.

```

## Solution Approaches

### O(N) - [[Python]] Naively Solving
- Well, time complexity is actually `O(N * K)` where k is the length of the longest string in array.
- But since the value of k << N its now considered as O(N)

```python 

def firstPalindrome(self, words: List[str]) -> str:
	for word in words: 
		if word==word[::-1]:
			return word
	return ""

```

### O(N) - CPP Implementing palindrome check

```cpp

string firstPalindrome(vector<string>& words) {
	for (int i = 0; i < words.size(); i++) {
		int low = 0;
		int high = words[i].size() - 1;
		if(high==0) return words[i]; 
		// single character words

		while (words[i][low] == words[i][high] and low <= high) {
			low++; high--;
		}
		if (low >= high) {
			return words[i];
		}
	}
	return "";
}


```

---

Return to [[DSA-Problems]]

---
