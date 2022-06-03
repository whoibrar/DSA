---
published : true

title :  "Number Manipulation"
permalink : "dsa/num-manipulation"
layout : note
excerpt : 

alias : 
categories : 
tags : 

# date : 2022-04-18 00:00:00 +0000

showfooter : 
showgraph : 
---

### Get the First Last Digit 

- First Digit 
	- `num%10`
- Last Digit
	- With Looping
		- `while(num>=10){n/=10;}`
	- Without Loop
		- CPP : `(int)(num / pow(10, (int)log10(num)))``
			- `log10(num)` -> no of digits in num
			- `pow(10,log10(num)` -> 10 * num

## Swapping

### Two numbers with third and reference

```cpp
void swapit(int &a, int &b) {
	int temp;
	temp = a;
	a = b;
	b = temp;
}
```

### Two elements of an vector or array

```cpp
vector<int> v = {0, 1, 2, 3};
swap(v[0], v[1]);
cout << v[0] << " " << v[1] << endl;

int arr[3] = {1, 2, 3};
swap(arr[0], arr[1]);
cout << arr[0] << " " << arr[1] << endl;
```


---

Return to [[DSA-Problems]]

---
