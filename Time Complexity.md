---
published : true

title : 
permalink : 
layout : note
excerpt : 

alias : 
categories : 
tags : 

# publishedDate : 2022-05-28 00:00:00 +0000

created_at: 2022-06-04 15:23:51 +0530
modified_at: 2022-06-04 15:23:51 +0530
---

### Time Complexity of loops 
source → [Analysis of Algorithms - Set 4 (Analysis of Loops) - GeeksforGeeks](https://www.geeksforgeeks.org/analysis-of-algorithms-set-4-analysis-of-loops/)
- No loop, recursion 
	- → O(1)
- Loop/recursion that runs constant number of times 
	- → O(1)
- Loop variable are inc/dec by constant amount 
	- → O(n)
- Loop variable are multiplied/divided by constant amount
	- → O(Logn)
- Loop variables are reduced/increased exponentially by constant amount
	- → O(LogLogn)
- Nested loops with x times innermost statement executed
	- → O(n^x)

### Consider Bottleneck Case as well
- Examples
	- [REC_CMPL1 | Interviewbit](https://www.interviewbit.com/problems/reccmpl1/)
- Where its a possibility they overtake the existing time complexity



### Continue Learning
- [Computational Complexity - YouTube](https://www.youtube.com/watch?v=moPtwq_cVH8) by [[MIT OCW]]
- [Big O: How Code Slows as Data Grows -  YouTube](https://www.youtube.com/watch?v=Ee0HzlnIYWQ) by [[FCC]]

---

Return to [[Algorithms|Algorithms]]

---
