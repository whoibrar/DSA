---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://leetcode.com/problems/first-unique-character-in-a-string/"
questionType : 

solvedDate : 2022-06-01 00:00:00 +0000
---

## Problem Statement

- Given a string `s`, _find the first non-repeating character in it and return its index_. If it does not exist, return `-1`.

### Example

```

Input : "leetcode"
Output : 0

```

## Solution Approaches

### O(N) sO(N) Character Frequency

- Use a simple 26 character vector/array to store frequencies
- Iterate through it again to find the first one that appears only once

```cpp

int firstUniqChar(string s) {
	vector<int> v (26, 0);
	for (int i = 0; i < s.length(); i++) {
		v[s[i] - 'a']++;
	}
	for (int i = 0; i < s.length(); i++) {
		if (v[s[i] - 'a'] == 1) {return i;}
	}
	return -1;
}

```

---

Return to [[DSA-Problems]]

---
