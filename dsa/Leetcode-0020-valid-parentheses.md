---
published : true

title : "Leetcode-0020-valid-parentheses"
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : 
questionType : 

solvedDate : 2022-06-09 10:30:07 +0530


created_at: 2022-06-09 10:30:49 +0530
modified_at: 2022-06-09 10:40:11 +0530
---

## Problem Statement

- Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
- An input string is valid if:
    - Open brackets must be closed by the same type of brackets.
    - Open brackets must be closed in the correct order.


### Example

```

Input: s = "()"
Output: true

Input: s = "()[]{}"
Output: true

Input: s = "(]"
Output: false

```

## Meta Data

### Link 

- [Valid Parentheses - LeetCode](https://leetcode.com/problems/valid-parentheses/)

### Tags 

- [[Stacks]]

### Similar 

- [[HR-balanced-brackets]]

## Solution Approaches

### O( N ) Using Stacks and +ve -ve pairing

- Solution from [[HR-balanced-brackets]]

```cpp

{% raw %}
unordered_map<char, int> sym = {{'(', -1}, {'{', -2}, {'[', -3}, {')', 1}, {'}', 2}, {']', 3}};
{% endraw %}

bool isValid(string s) {
	stack<char> st;
	for (auto i : s) {
		if (sym[i] < 0) {
			st.push(i);
		} else {
			if (st.empty()) {return false;}
			char recent = st.top(); st.pop();
			if (sym[i] + sym[recent] != 0 ) {
				return false;
			}
		}
	}
	if (st.empty()) {return true;}
	return false;
}


```

### O(N) Directly Pairing Brackets to each other

```python

def isValid(self, s: str) -> bool:
	stack = []

	i = 0
	while(i<len(s)):
		if s[i] in '({[':
			stack.append(s[i])
		else:
			if len(stack)==0:
				return False
			elif ((stack[-1]=='(' and s[i]==')') or (stack[-1]=='[' and s[i]==']') or (stack[-1]=='{' and s[i]=='}')):
				stack.pop()
			else:
				return False
		i+=1
	if not stack:
		return True
	return False

```

Another Implementation 

```python

arr = []
pairs = {"[":"]", "{":"}", "(":")"}

for a in s:
	if a in pairs:
		arr.append(a)
	elif len(arr)!=0 and a == pairs[arr[-1]]:
		arr.pop()
	else :
		return False

if len(arr)==0:
	return True
else:
	return False

```

---

Return to [[DSA-Problems]]

---
