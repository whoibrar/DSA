---
published : true

title : "Bit Manipulation"
permalink : "dsa/bit-manipulation"
layout : note
excerpt : 

alias :
categories : 
tags : 

# date : 2022-04-18 00:00:00 +0000

showfooter : 
showgraph : 
---

## Basics
### Bitwise NOT [ ~ ]

- Flips the bits
	- zeros -> ones
	- ones -> zeros
- It is Ones Complement of a number

```
 5 -> 101
~5 -> 010

```

### Bitwise AND [ & ]

- True if and only if both are true, else false

### Bitwise OR [ | ]

- True if any one is true

### Bitwise XOR [ ^ ]

- True if only one is True.

### Left Shift [ << ]

- `1<<n = 2^n`

### Right Shift [ >> ]

- `n>>k = n/(2^k)`
















### Resources

- [Bit Twiddling Hacks](https://graphics.stanford.edu/~seander/bithacks.html)
- [Basics of Bit Manipulation Tutorials & Notes - Basic Programming - HackerEarth](https://www.hackerearth.com/practice/basic-programming/bit-manipulation/basics-of-bit-manipulation/tutorial/)
- [Find most significant set bit of a number - GeeksforGeeks](https://www.geeksforgeeks.org/find-significant-set-bit-number/)
- [Basics of Bit Manipulation Tutorials & Notes | Basic Programming | HackerEarth](https://www.hackerearth.com/practice/basic-programming/bit-manipulation/basics-of-bit-manipulation/tutorial/)
- [Bits manipulation (Important tactics) - GeeksforGeeks](https://www.geeksforgeeks.org/bits-manipulation-important-tactics/)
- [6 Amazing BIT Manipulation Ticks You must Know | CP Course | EP 49 - YouTube](https://www.youtube.com/watch?v=XjtYsFjXtoE)
- [Algorithms 101: the basics of Bit Manipulation explained](https://www.educative.io/blog/bit-manipulation-algorithm)
- [Bit Manipulation (Complete Guide) - InterviewBit](https://www.interviewbit.com/blog/bit-manipulation/)
- [That XOR Trick](https://florian.github.io/xor-trick/)
- 
- 

## Bit Hacks and Tricks

### XOR with Zero One Self

- `n^n=0`
- `n^0=n`
- `n^1 = probably nothing interesting :(`

### Find if Odd or Even

- `(num & 1)` gives 1 for odd numbers only

### Multiply or Floor Divide by powers of 2

- `(num>>n)` divides by `2^n`  
- `(num<<n)` multiplies by `2^n`

### Check if power of 2

- `num&(num-1)` shall result in false.
- As seen in [[Leetcode-0231-power-of-two]]

### Find Neighboring Numbers

- Odd xor 1 gives `odd-1`
- Even xor 1 gives `even+1`

```cpp 

// How it Works

// 0b1001 --> odd
// 0b0001 --> 1 
// 0b1000 --> on xor

// 0b1000 --> even
// 0b0001 --> 1 
// 0b1001 --> on xor


```

### Swap 2 Nos without 3rd 

```cpp

x = x ^ y; 
y = x ^ y;
x = x ^ y;

```

### Swap 3 Nos without 4th 

```cpp

a = a ^ b ^ c;
b = a ^ b ^ c;
c = a ^ b ^ c;
a = a ^ b ^ c;

```

### Check +ve -ve zero

```cpp

int sign(int n) {
	return ((n >> 31) - (-n >> 31));
}

// (n >> 31) 
// -ve -> -1
//   0 -> 0
// +ve -> 0

// (-n >> 31)
// -ve -> 0
//   0 -> 0
// +ve -> -1

// (n>>31) - (-n>>31)
//    0    -  (-1)  <- +ve
//    0    -   0    <- 0
//   -1    -   0    <- -ve
```

### Find Rightmost Set Bit

```
n&(~(n-1)) <- binary number
Log2(above) <- position

1011 <-  (n-1)
1100 <-   n
0100 <- ~(n-1)
----
0100 <- n & ~(n-1)
```

