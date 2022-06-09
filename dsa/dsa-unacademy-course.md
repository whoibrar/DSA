---
published : false

title : 
permalink : 
layout : note
excerpt : Notes and Problems list

alias : 
categories : 
tags : 

# publishedDate : 2022-05-16 00:00:00 +0000

showfooter : 
showgraph : 
created_at: 2022-06-03 18:15:21 +0530
last_modified_at: 2022-06-03 18:15:21 +0530
---

## Links
- [Data Structures and Algorithms By LoveBabbar](https://unacademy.com/goal/data-structures-algorithms-dsa/GRZCK/planner)

# Class Notes

## Programming basics - III  [21Apr2022]

- List of problems 
	- [[Leetcode-0231-power-of-two]]
	- [[Leetcode-0476-number-complement]]
	- [[Leetcode-0007-reverse-integer]]

## Functions and Arrays [23Apr2022]

- List of problems
	- [[GFG-Searching-a-number]] aka Linear Search in An Array.
	- [[GFG-reverse-an-array]].
	- [[GFG-find-minimum-and-maximum-element-in-an-array]].
	- [Shuffle the position of each Array element by swapping adjacent elements - GeeksforGeeks](https://www.geeksforgeeks.org/shuffle-the-position-of-each-array-element-by-swapping-adjacent-elements/).
	- [[Leetcode-0075-sort-colors]] aka Sort Array of 0, 1 and 2.
	- [[GFG-move-all-negative-elements-to-end]].
	- [[Leetcode-0189-rotate-array]] #wip 
	- [[GFG-cyclically-rotate-an-array-by-one]] 
	- [[Leetcode-0287-find-the-duplicate-number]]
	- [Program to check if an Array is Palindrome or not - GeeksforGeeks](https://www.geeksforgeeks.org/program-to-check-if-an-array-is-palindrome-or-not/)
	- [[Leetcode-0001-two-sum]]
	- [[Leetcode-0015-3sum]]
	- [[Leetcode-1207-unique-number-of-occurrences]]
	- 
	- 

## Arrays Problems II [28Apr2022]

- [Minimum swaps required to bring all elements less than or equal to k together - GeeksforGeeks](https://www.geeksforgeeks.org/minimum-swaps-required-bring-elements-less-equal-k-together/)
- [Minimum swaps and K together | Practice | GeeksforGeeks](https://practice.geeksforgeeks.org/problems/minimum-swaps-required-to-bring-all-elements-less-than-or-equal-to-k-together4847/1/)


- List of Problems
	- [[GFG-common-elements]]
	- [[GFG-first-repeating-element]]
	- [[GFG-first-non-repeating-element]]
	- [[Leetcode-0387-first-unique-character-in-a-string]]
	- Pending 
	- [[GFG-subarray-with-equal-zero-and-one]]
	- Find subarray with 0 sum in array
	- Find factorial of large number
	- Minimum platforms problem
	- Minimise heights II 
	- Majority element in array
	- Arrray subset of another array


```cpp

int minSwap(int arr[], int n, int k) {
	
	// counting values less than k
	int count = 0;
	for (int i = 0; i < n; i++) {
		if (arr[i] <= k) {count++;}
	}

	// counting inital window elements more than k
	int more=0;
	for(int i=0;i<count;i++){
		if(arr[i]>k){bad++;}
	}

	// traversing window until end
	int optimal = more;
	int start = 0, end=count;
	while(end<n){
		if(arr[i])

	}

}

int main() {
	int arr[] = {2, 1, 5, 6, 3};
	minSwap(arr, 5, 3);
}

```


## Sorting Techniques [10May2022]

- Sorting : Arranged in monotonic order
- Sorting Algorithms
	- [[algo.sort.selection|Selection Sort]]
	- [[algo.sort.bubble|Bubble Sort]]
	- [[algo.sort.insertion|Insertion Sort]]
		- #hw what does the defualt sorting algorithm use ?
		- #hw cyclically rotate by 2




## Pointers - I [18May2022]

- symbol table 
	- used for mapping variables to their associated memory address.
- `&a` here `&` is address of operator
	- output is in hexadecimal location
- pointer -> stores address 
- How does the compiler know that it is `4bytes` of single `int` or `4bytes` of multiple `char`?
	- #search 

```cpp

int i = 5;
int *p_i = &i;

string s = "hello";
string *p_s = &s;

int a[3] = {1, 2, 3};
int (*p_a)[3] = &a;

cout << "size " << "address " << "direct " << "val " << endl;
cout << sizeof(p_i) << " " << &p_i << " " << p_i << " " << *p_i << endl;
cout << sizeof(p_s) << " " << &p_s << " " << p_s << " " << *p_s << endl;
cout << sizeof(p_a) << " " << &p_a << " " << p_a << " " << *p_a << endl;

// size address direct val 
// 4 0x61fef4 0x61fef8 5
// 4 0x61fed8 0x61fedc hello
// 4 0x61fec8 0x61fecc 0x61fecc

```

- #hw why size of pointer varies across different architecture of system ?
	- 64bit -> 8 and 32bit -> 4
- `* p` -> dereference operator 


```cpp

// if you just want to declare a pointer 

int *p; 
//don't do this 
// it could point to anything in memory
// maybe also from read-only-space as well 

int *p = 0; 
p = &a;
// declare first to a 
// NUll pointer
// later change to appropriate

// this is better as it will point to a safe memory location

```

- Dangling Pointer -> one that points to a random memory location 
- Self Referencing Pointer -> #search 

- `arr[i] = *(arr + i)` 
- `i[arr] = *(i +arr)`

- passing array as pointer


```cpp

void pass_arr_with_ptr(int (*p)) {
	for (int i = 0; i < 3; i++) {
		cout << *(p + i) << " ";
	}
	// prints the values of array to which p is pointing
	// 1 2 3
}

int main() {
	int arr[] = {1, 2, 3};

	int *p = arr;
	func(p);

	cout << "arr[i]  *(arr+i)  i[arr]  " << endl;
	for (int i = 0; i < 3; i++) {
		cout << arr[i] << "         " << *(arr + i) << "         " << i[arr] << endl;
	}
	// arr[i]  *(arr+i)  i[arr]  
	// 1         1         1
	// 2         2         2
	// 3         3         3


}

```

```cpp

void pass_arr_with_ptr(int (*p)) {
	cout << "in func " << "p->" << p << " | &p->" << &p << endl;
}

int main() {
	int arr[] = {1, 2, 3};

	int *p = arr;
	cout << "in main " << "p->" << p << " | &p->" << &p << endl;
	pass_arr_with_ptr(p);
}
// in main p->0x61ff04 | &p->0x61ff00
// in func p->0x61ff04 | &p->0x61fef0

// even though p inside func contains the same adrs
// itself has a different adrs, so its a copy of the orginal
// only the pointer to adrs is copied

```

- typeof() in cpp #search 


```cpp

// different behaviours with int and char araays

int arr[] = {1, 2, 3, 4};
int *p = arr;
cout << p << endl;
// 0x61fef8
// prints hexadecimal adrs 

char ch[] = "abcd";
char *ptr = ch;
cout << ptr;
// abcd
// prints the entire ch array

char alpha = 'a';
char *ctr = &alpha;
cout << ctr << endl;
// a<0x01>
// weird output
```
- because cout is implemented diffently for each of them.
- in case of character cout prints until it finds null character



## Pointers - II [19May2022]

- Why do we need double pointers ?
- how many levels deep can you go with pointers ?


## Basic Math for DSA [14May2022]

- Prime Number 
	- 2->n check if divisible 
		- can optimize by checking until 2->(n/2)
		- or also sqrt(n)
	- Sieve of erathoneses #hw 
	- Leetcode count no of primes
- #hw segmented sieve 
	- find prime numbers in a given range
- GCD 
	- euclids algo  #hw 
	- `gcd(a,b) = g(a-b,b)`
	- `gcd(a,b) = g(a%b,b)`
	- 

- check for even with `n&1==0` 





## Static Dynamic Allocation [21May2022]

- Reference Variable : Same Memory Different Name

```cpp

void pass_var(int pv) {
	cout << "pv : " << pv << " | &pv : " << &pv << endl;
}
void pass_ptr(int *pp) {
	cout << "pp : " << pp << " | &pp : " << &pp << endl;
}

void pass_ref(int &pr) {
	cout << "pr : " << pr << " | &pr : " << &pr << endl;
}

int main() {

	// variable
	int i = 5;
	cout << "i : " << i << " | &i : " << &i << endl;

	// pointer
	int *p = &i;
	cout << "p : " << p << " | &p : " << &p << endl;

	// reference
	int &r = i;
	cout << "r : " << r << " | &r : " << &r << endl;

	cout << endl;

	pass_var(i);
	pass_ptr(p);
	pass_ref(r);

	// i : 5 | &i : 0x7ffd076e2264
	// p : 0x7ffd076e2264 | &p : 0x7ffd076e2268
	// r : 5 | &r : 0x7ffd076e2264

	// pv : 5 | &pv : 0x7ffd076e224c
	// pp : 0x7ffd076e2264 | &pp : 0x7ffd076e2248
	// pr : 5 | &pr : 0x7ffd076e2264

	// only variable, reference-variable , passed-reference-varible have same memory address
}

```

- why can't use pointer instead of reference ?
	- #hw gfg link in discord
- memory allocation 
	- static 
	- dynamic
- dynamic array allocation 
	- `new int` 
		- creates a new block in heap memory
	- `int * ptr = new int`
		- dynamic new int is created in heap memory
		- to which a pointer is associated which is created in stack memory
- `int * arr = new int`
	- this is dynamic memory allocation for array
- memory leakage 

```cpp 

// this uses only 4bytes of memory
// cause the num variable is being created when entering scope of loop
// and destroyed when moving out of scope 
// because num was statically allocated

while(true){
	int num = 5;
}

// this uses infinite memory 
// 

while(true){
	int * ptr = new int;
}

```

- #hw 
	- why does heap memory dosent' get auto destroyed 
	- and why it does in stack 
	- why can't be pointer be allocated in heap

```cpp

// deleting heap memory
// free-up memory

int * ptr = new int;
delete ptr;

int * arr = new int[5];
delete []arr;

// this []arr is syntax perefence instead of arr[] 
```

- #hw void pointer 
	- `void * ptr` can point to any data type
	- why do we need this 

```cpp

// creating accessing deleting dynamic array

int n;
cin >> n;

// declare dynamic array 
int *arr = new int[n];

// adding to array
for(int i=0;i<n;i++){
	cin >> arr[i];
}

// print

for(int i=0;i<n;i++){
	cout <<  arr[i] << " ";
}

delete []arr;

```

```cpp

int m, n;
cin >> m >> n;

// int * ptr = new int[n];
// creates pointer to array
// [ptr] --> [ | | | | ]

int **arr = new int *[m];
// creates pointer-array
// |   <-arr->   | <- only this part
// |      ^      |    is created for now
// |      |      |
// |      |      |	| <-add later-> |
// |   [int *]   |  |  [ | | | ]  |
// |   [int *]   |  |  [ | | | ]  |
// |   [int *]   |  |  [ | | | ]  |


for (int i = 0; i < m; i++) {
	arr[i] = new int[m];
}
// |   <-arr->   |  new array is created for
// |      ^      |  each element of arr
// |      |      |
// |   [int *]   | --> [ | | | ]
// |   [int *]   | --> [ | | | ]
// |   [int *]   | --> [ | | | ]

// input
// 3 4
// 1 2 3 0
// 4 5 6 1
// 7 8 9 0
for (int i = 0; i < m; i++) {
	for (int j = 0; j < n; j++) {
		cin >> arr[i][j];
	}
}

// output
// 1 2 3 0 
// 4 5 6 1 
// 7 8 9 0 
for (int i = 0; i < m; i++) {
	for (int j = 0; j < n; j++) {
		cout << arr[i][j] << " ";
	}
	cout << endl;
}

// deleting
for (int i = 0; i < m; i++) {
	delete []arr[i];
}
delete []arr;

// jagged array

int m;
cin >> m;

int size[] = {3, 2, 4, 3};

int **jag = new int*[m];

for (int i = 0; i < m; i++) {
	jag[i] = new int[size[i]];
}


for (int i = 0; i < m; i++) {
	for (int j = 0; j < size[i]; j++) {
		cin >> jag[i][j];
	}
}

for (int i = 0; i < m; i++) {
	for (int j = 0; j < size[i]; j++) {
		cout << jag[i][j] << " ";
	}
	cout << endl;
}

// input 
// 4
// 1 2 3
// 4 5 
// 1 2 3 4
// 7 8 9 

// output
// 1 2 3
// 4 5 
// 1 2 3 4
// 7 8 9 
```


- Rachit Jain 
	- [DataStructures-Algorithms/template_demo.cpp at master · rachitiitr/DataStructures-Algorithms](https://github.com/rachitiitr/DataStructures-Algorithms/blob/master/Library/Miscellanious/template_demo.cpp)
	- [DataStructures-Algorithms/template.cpp at master · rachitiitr/DataStructures-Algorithms](https://github.com/rachitiitr/DataStructures-Algorithms/blob/master/Library/Miscellanious/template.cpp)
- 

- Macro 
- `#include <iostream>` -> preprocessor file 
- `#define PI 3.14` -> piece of code that is replaced by something
	- why not use variable ?
		- uses space 
	- macro doesn't use space
		- before compiling it changes all the occurences
	- its replacement and not storing 
	- Disadvantages #hw 
		- macros for cp #hw 
- function like macro definition #hw 
- for loop macro #hw 

- Global Variable 
	- bad why 
		- cause anyone can modify
- constant variable 

- inline functions 
	- used to reduce function call overhead
	- works for smaller functions 
		- for one line valid 
		- 2 or 3 compiler depends
		- >3 can't replace 
	- function call is replaced by function body
	- how to know if it got replaced #hw 
	- 

- Default arguments 
	- passed from right to left otherwise gives error 
- how does pointer point to address in memory
	- what are the limits ?
- how does program relate to ram to address 


## Recursion - I [[25May2022]]

- also watch 
	- fcc 
	- codehelp recursion playlist

- Recursion : Function calling itself
	- Breaking down bigger problem into similar smaller ones
	- Base Case : where the recursion stops aka terminating condition
		- only case where the solution to problem is provided else are calculated
- Types of Recursion
	- Tail Recursion
		- when recursive call is at after the processing
	- Head Recursion
		- when recursive call is before the processing
- Basis Rule for Solving recursion problems 
	- Solve one case and else leave to recursion

### Recursively print 1->n and n->1
```cpp

void print(int a) {
	if (a < 1) {
		return;
	}
	cout << a << " "; // 5 4 3 2 1
	// Head Recursion
	
	print(a - 1);
	cout << a << " "; // 1 2 3 4 5
	// Tail Recursion
}

int main() {
	print(5);
}


```

### Recursively Find Max in Array

#try search similarly but starting through `arr[0]` and calling recursively on `arr[1]`

```cpp

int finmax(int arr[], int n) {
	if (n == 1) {
		return arr[0];
	}
	return max(arr[n - 1], finmax(arr, n - 1));
}

int main() {
	int arr[] = {4, 2, 6, 9, -34, 0, 12};
	cout << finmax(arr, 7);
}

```

### Fast exponentiation 2^n
 
 ```cpp

int expo(int n) {
	int sign = 1;

	if (n < 0) {sign = -1; n = n * sign;}
	if (n == 0) {return 1;}
	if (n == 1) {return 2;}

	int ans = expo(n / 2); ans *= ans;
	if ((n & 1) == 1) {ans *= 2;}

	return ans * sign;
}

```

- Problems Solved
	- [[GFG-modular-exponentation-for-large-numbers]]
	- [[CHF-FEXP-fast-exponentiation]]


## Recursion - II [[26May2022]]
- List of Problems
	- [[GFG-optimal-strategy-for-a-game]]
	- [[IB-subset-sum-problem]]
	- [[GFG-coin-change]]


- NPTEL DP Algo
	- [Computer Sc - Design & Analysis of Algorithms - YouTube](https://www.youtube.com/playlist?list=PL7DC83C6B3312DF1E)
	- 16-19 DP

### Recursive Induction

```

let f(n) be a recursive func

1. Show f(1) works				-> base case
2. Assume f(n-1) works			-> recursive leap of faith
3. Show f(n) works using f(n-1) -> knocing off dominos from first to last


```

### 5 Steps for Solving Recursive Problems

Video : [5 Simple Steps for Solving Any Recursive Problem - YouTube](https://www.youtube.com/watch?v=ngCos392W4w)

- 1 What's Simplest Possible input ?
	- This is useful for finding the base case.
	- Only case where solution is explicitly provided, all other cases are build using base case.
- 2 Play Around with examples and visualize 
	- How output changes with different inputs
	- Try similar examples and that better helps in deducing for general case
- 3 Relate bigger problem to simpler cases
	- Finding relations and patterns between cases.
	- Can `f(5)` be solved using `f(4)`.
- 4 Generalize the pattern
- 5 Combining recursive pattern with base case

> How to Solve The Recursive Problem: Solve the recursive problem.


- Recursive leap of faith
	- Assume simpler cases just work out!
	- Thinking of only but the base case


## Character Arrays & Strings [12May2022]

- `char` uses 1byte and is stored using ASCII encoding.

```cpp

char name[4];
cin >> name;

[ J | O | H | N | '\0' ]

```

### `int arr` vs `char arr`
- size of array with n elements
	- int arr -> `n*4` as each element is 4bytes
	- char arr -> `n` as each element is 1byte
- Null Character is added at end of char array

### `char arr` vs `strings`
- Changing Size 
	- size is statically defined in char arr
	- size is dynamic in `string`, using `push_back()`
- Speed of Running
	- implementation of `char arr` is faster

- `cin >> s` where s is declared as string reads input until it finds a delimiter (space, newline, tab)

```cpp  
string s;  
cin >> s; //what the f?  
cout << s; //what  

string x;
getline(cin, s); //what the f?
cout << s; //what the f?
```

### Given two strings, find if they are anagrams ?
- Frequency array with 26 Characters length
- For each element, Increment counter with first string, decrement with second string
- If the final values in frequency array are all zeros then its an anagram

```cpp

bool isAngram(string a, string b) {
	int count[26];
	for (int i = 0; i < 26; i++) {
		count[i] = 0;
	}

	for (int i = 0; i < getlen(a); i++) {count[(a[i]) - 'a']++;}
	for (int i = 0; i < getlen(b); i++)	{count[(b[i]) - 'a'] -= 1;}

	for (int i = 0; i < 26; ++i) {
		if (count[i] != 0) return false;
	}

	return true;
}

int getlen(string arr) {
	int len = 0;
	while (arr[len] != '\0') {
		len++;
	}
	return len;
}

void reverse(char name[]) {
	cout << name << endl;
	int start = 0, end = getlen(name) - 1;
	while (start < end) {
		swap(name[start], name[end]);
		start++;
		end--;
	}
	cout << name << endl;
}

```

### #hw 
- Problems from discord server
- minimum no of flips for binary string to convert it to alternating binary string
- find string a in string b
- strings are rotated find if they are same
- cppreference
- npos and string find method
	// strln -> gives len
	// strcmp -> return 0 if both equal else something else
	// strcpy -> copies first string into second
	// getline -> can also set custom delimiter

- [char* vs std:string vs char[] in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/char-vs-stdstring-vs-char-c/)
- [C++ Strings: Using char array and string object](https://www.programiz.com/cpp-programming/strings)
- [Array of Strings in C++ - 5 Different Ways to Create - GeeksforGeeks](https://www.geeksforgeeks.org/array-of-strings-in-cpp-5-different-ways-to-create/)
- [strcmp() in C/C++ - GeeksforGeeks](https://www.geeksforgeeks.org/strcmp-in-c-cpp/)



## Recursion III []


- Can't create subsets
	- [[CPP Doubts#Why cant I create Subsets]]