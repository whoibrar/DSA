---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://leetcode.com/problems/reverse-integer/"
questionType : 

solvedDate : 2022-05-16 00:00:00 +0000
---

## Problem Statement

- Given a signed 32-bit integer `x`, return `x` _with its digits reversed_. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-231, 231 - 1]`, then return `0`.

### Example

```

Input: x = 123
Output: 321

```

## Solution Approaches

### O(N) - Intuitively Extracting Last digit 

- Extract the last digit from the number, add it to 10 times of previous ans, divide the given number by 10.
- No need to check for sign
	- As `123 % 10 = 3` and `-123 % 10 = -3`
- Before every operation check for overflow
	- `ans*10 > INT_MAX` can be written as `ans>INT_MAX/10`
	- This avoids overflow error.

```cpp

int reverse(int x) {
int ans = 0;

while (x) {
	if ( ans > (INT_MAX / 10) || ans < (INT_MIN / 10) ) {
		return 0;
	}
	
	ans = ans * 10 + (x % 10);
	x = x / 10;
}

return ans;
}

```


---

Return to [[DSA-Problems]]

---
