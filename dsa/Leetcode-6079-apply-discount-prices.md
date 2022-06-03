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

- You are given a string `sentence` representing a sentence and an integer `discount`. For each word representing a price, apply a discount of `discount%` on the price and **update** the word in the sentence. All updated prices should be represented with **exactly two** decimal places.
- For example, `"$100"`, `"$23"`, and `"$6.75"` represent prices while `"100"`, `"$"`, and `"2$3"` do not.

### Example

```

Input: sentence = "there are $1 $2 and 5$ candies in the shop", discount = 50
Output: "there are $0.50 $1.00 and 5$ candies in the shop"
Explanation: 
The words which represent prices are "$1" and "$2". 
- A 50% discount on "$1" yields "$0.50", so "$1" is replaced by "$0.50".
- A 50% discount on "$2" yields "$1". Since we need to have exactly 2 decimal places after a price, we replace "$2" with "$1.00".

```

## Solution Approaches

### Uhhh! Why Can't I Just Make it work

- Not my proudest!
	- This was part of [Weekly Contest 295 - LeetCode](https://leetcode.com/contest/weekly-contest-295/).
	- Started with the first approach I could think of and that [cost me a little too much](https://i.imgur.com/kVkM7t9.png), after every submission I would get an edge case for which I made quick fix only to break again in next submission, this happened not once, not twice, not even thrice but fucking 10 times. 
	- Soon, Time was up and I spent all my time on a single problem and couldn't even solve it : (
	- Sat through after the contest ended and somehow made it work!

```python

class Solution:
    def discountPrices(self, sentence: str, discount: int) -> str:
        
        words = sentence.split(' ')
        ans=''
        
        for word in words:
            if(word[0]!='$'):
                ans=ans+" "+word
                # word that doesn't start with $ 
                # is added directly
                
            else:
                
                # This flag checks for edge cases
                isNum=True
                
                # 2$3 or $45$
                for i in word[1:]:
                    if i not in "1234567890.":
                        isNum=False
                
                # $
                if(len(word)==1):
                    isNum=False
                
                
                if(isNum==False):
                    ans=ans+" "+word
                
                else:
                    # all filteration is done 
                    # any word reaching this section is 
                    # actual price that satisfies given conditions
                    
                    num=float(word[1:])*100
                    # multiplying by 100 before to avoid floating point arthematic
                    
                    
                    afterdiscount = num-((num*discount)/100)
                    
                    strtoadd = str(afterdiscount).split('.')[0]
                    
                    if(len(strtoadd)==1):
                        strtoadd='00'+strtoadd
                    
                    # evaluating before decimal and after decimal parts seperately
                    
                    bf = strtoadd[:-2] or '0' # when None is returned
                    af = strtoadd[-2:]
                    
                    # to satisfy 2digit precision condition
                    if len(af)==1:
                        af+='0'
                    
                    ans = ans + " $"+bf+"."+af
        return ans[1:] 
        # unwanted space is added before the first word 

```



### Other Better Solutions
- Split into sentence into individual word
- Check if it a price satisfying given condition
	- Apply the discount
- Add to answer.

```python

# Submission by https://leetcode.com/wwwwodddd/
def discountPrices(self, s: str, d: int) -> str:
	s = s.split()
	for i in range(len(s)):
		if len(s[i]) > 1:
			if s[i][0] == '$' and s[i][1:].isdigit():
				s[i] = '$%.2f' % (float(s[i][1:]) * (1 - d / 100))
	return ' '.join(s)

# Submission by https://leetcode.com/elimsamazak/
def discountPrices(self, sentence: str, discount: int) -> str:
	def isNum(s):
		try:
			return float(s)
		except:
			return None

	ans = []
	for w in sentence.split():
		if w[0] == '$' and isNum(w[1:]):
			x = isNum(w[1:])
			x *= (1 - discount/100)
			ans += [ f"${x:.2f}" ]
		else:
			ans += [w]
	return " ".join(ans)

```



---

Return to [[DSA-Problems]]

---