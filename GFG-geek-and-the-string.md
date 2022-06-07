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

solvedDate : 2022-05-29 00:00:00 +0000
---

## Problem Statement

- Remove all the consecutive duplicate pairs and concatenate the remaining string to replace the original string.
- Our geek loves to play with strings, Currently, he is trying to reduce the size of a string by recursively removing all the consecutive duplicate pairs. In other words, He can apply the below operations any number of times.
- Your task is to find the string with minimum length after applying the above operations.

### Example

```
Input : aaabbaaccd
Output : ad

Explanation :
	(aa)abbaaccd
	a(bb)aaccd
	(aa)accd
	a(cc)d
	ad



```

## Solution Approaches

### O(N^k) String Slicing and Building

- `K-1` is the duplicate pairs count
- `s[:i]+s[i+2:]` rebuilds s without duplicated pair
- after every duplicate found move a index back by one!
	- `index=0` is the edge case

```python

def removePair(self,s):
	i=0
	while(i+1<len(s)):
		if(s[i]==s[i+1]):
			s=s[:i]+s[i+2:]
			if(i!=0):
				i-=1
		else:
			i+=1
	if(s!=''):
		return s
	else:
		return "Empty String"
		# returning an empty string, None 
		# was resulting in wrong answer
		# and apparently this works 
		# weird, but okay!

```

---

Return to [[DSA-Problems]]

---
