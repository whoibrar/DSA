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

solvedDate : 2022-06-08 23:03:46 +0530


created_at: 2022-06-08 23:09:45 +0530
modified_at: 2022-06-08 23:09:45 +0530
---

## Problem Statement

- Our Monk loves candy!
- While taking a stroll in the park, he stumbled upon N Bags with candies. The i'th of these bags contains Ai candies.
- He picks up a bag, eats all the candies in it and drops it on the ground. But as soon as he drops the bag, the number of candies in the bag increases magically! Say the bag that used to contain X candies (before eating), now contains [X/2] candies! ,where [x] is the greatest integer less than x (Greatest Integer Function).
- Amazed by the magical spell, Monk can now have a lot more candies! But he has to return home in K minutes. In a single minute,Monk can consume all the candies in a single bag, regardless of the number of candies in it.
- Find the maximum number of candies that Monk can consume. 

### Example

```

bag = [2,1,7,4,2]

The state of bags is:
2 1 7 4 2
Monk eats all candies from Third bag (7). The state of bags becomes:
2 1 3 4 2
Monk eats all candies from Fourth bag (4). The state of bags becomes:
2 1 3 2 2
Monk eats all candies from Third bag (3). The state of bags becomes:
2 1 1 2 2
Hence, the Monk eats 7+4+3= 14


```

## Meta Data

### Link 

- [Monk and the Magical Candy Bags](https://www.hackerearth.com/practice/data-structures/trees/heapspriority-queues/practice-problems/algorithm/monk-and-the-magical-candy-bags/)

### Topics 

- [[Heaps]]
- [[Prority Queues]]
- [[Multiset]]

## Solution Approaches

### O(N) Using Multiset

- Get the biggest element of set, add it to ans 
- Also add half the value of max element back to the set

```cpp

int main(){
	int t; cin >> t;
	while (t--) {
		int n, k; cin >> n >> k;
		
		// making the set
		multiset<long long> bags;
		for (int i = 0; i < n; i++) {
			long long count; cin >> count;
			bags.insert(count);
		}
		
		// main code block
		long long total = 0;
		for (int i = 0; i < k; i++) {
			
			// get iterator to last element of set
			auto last_it = bags.end(); last_it--;
			long long count = *last_it;
			
			// add max value to total 
			// remove it from set 
			// add max/2 back to set
			total += count;
			bags.erase(last_it);
			bags.insert(count >> 1);
		}
		cout << total << endl;
	}
}

```


---

Return to [[DSA-Problems]]

---
