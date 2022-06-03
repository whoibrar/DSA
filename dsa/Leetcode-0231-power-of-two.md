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
questionType : "Bit Manipulation"

solvedDate : 2022-05-14 00:00:00 +0000
---

## Problem Statement

- Given an integer `n`, return _`true` if it is a power of two. Otherwise, return `false`_.
- An integer `n` is a power of two, if there exists an integer `x` such that `n == 2x`.

### Example

```
given 16
return true

as 2**4 = 16
```

## Solution Approaches

### O(1) | Bit Manipulation

- Numbers less than 1 can't be powers of two.
- Powers of 2 in binary are represented as single 1 with followed with zeros.
- and number one lesser than power of 2 is all 1's.
- So applying `and operation` on power of 2 and number one lesser than it should result in zero.

```cpp 
bool isPowerOfTwo(int n) {
	if (n<1) return false;
	return (n&(n-1))==0;	
}

// say n = 8 
// ...1000 --- n
// ...0111 --- n-1
// ...0000 --- (n&(n-1))
```

## Related

---

Return to [[DSA-Problems|DSA Problems]]

---