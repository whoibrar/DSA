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

solvedDate : 2022-06-09 10:22:56 +0530


created_at: 2022-06-09 10:24:24 +0530
modified_at: 2022-06-09 10:27:49 +0530
---

## Problem Statement

- Given strings of brackets, determine whether each sequence of brackets is balanced. If a string is balanced, return YES. Otherwise, return NO.

### Example

```

Input :

{[()]}
{[(])}

Output :

YES
NO

Explanation :

- The string {[()]} meets both criteria for being a balanced string.
- The string {[(])} is not balanced because the brackets enclosed by the matched pair { and } are not balanced: [(]).


```

## Meta Data

### Link 

- [Balanced Brackets - HackerRank](https://www.hackerrank.com/challenges/balanced-brackets/problem)

### Tags 

- [[Stacks]]

## Solution Approaches

### O( N ) Using Stacks and +ve -ve Brackets 

- Assign -ve values to opening brackets and positive to closing
- For any opening bracket push it to the stack and for closing compare with the top most element in stack


```cpp


#include <bits/stdc++.h>
using namespace std;

{% raw %}
unordered_map<char, int> sym = {{'(', -1)}, {.'{', -2}, {'[', -3}, {')', 1}, {'}', 2}, {']', 3}};
{% endraw %}

string isBalanced(string s) {
	stack<char> st;
	for (auto i : s) {
		if (sym[i] < 0) {
			st.push(i);
		} else {
			if (st.empty()) {return "no";}
			char recent = st.top(); st.pop();
			if (sym[i] + sym[recent] != 0 ) {
				return "no";
			}
		}
	}
	if (st.empty()) {return "yes";}
	return "no";
}

int main() {
	int n; cin >> n;
	while (n--) {
		string s; cin >> s;
		cout << isBalanced(s) << endl;
	}
}


```


---

Return to [[DSA-Problems]]

---
