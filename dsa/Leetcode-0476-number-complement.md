---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://leetcode.com/problems/number-complement/"
questionType : "Bit Manipulation"

solvedDate : 2022-05-14 00:00:00 +0000
---

## Problem Statement

- Given a Number, Find its complement
- Complement of number can be achieved by flipping 0's to 1's and vice versa. 

### Example

```
given 5
return 2

5 in binary is 101
5's complement is 010
010 in decimal is 2
```

## Solution Approaches

### O(1) - Bitwise Using Mask

- Create a Mask that has all zeros until the set bit and later all ones
- Find the Complement of given number using [[operator.onesComplement|Ones Complement Operator]] 
- Use `and operator` to get the final result 

```cpp
int findComplement(int num) {
	int mask = 0;
	
	while(mask<num){
		mask = (mask<<1) | 1;
	}
	
	return (~num)&mask;
}

// while loop 
// ... 0000 0000 on applying <<1
// ... 0000 0000 on applying | 1
// ... 0000 0001 on applying <<1
// ... 0000 0010 on applying | 1
// ... 0000 0011 ... and so on


```

## Related

---

Return to [[DSA-Problems|DSA Problems]]

---