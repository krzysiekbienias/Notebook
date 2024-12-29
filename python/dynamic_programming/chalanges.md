# House Robber
| Title        | Source   | Data Structure | Algo Concept                   | Difficulty | Time Complexity | Space Complexity |
|--------------|----------|----------------|--------------------------------|------------|-----------------|------------------|
| House Robber | leetcode | array          | Dynamic programming /recursion | Medium     |complete

* Input: ```nums = [2,7,9,3,1]```
* Output: 12
* Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
    
    Total amount you can rob = 2 + 9 + 1 = 12.


```python
def rob(self, nums: List[int],i=0,lookup=None) -> int:
        lookup={} if lookup is None else lookup
        if i in lookup:
            return lookup[i]
        if i>=len(nums):
            return 0
        else:
            lookup[i]=max(nums[i]+self.rob(nums,i+2,lookup),self.rob(nums,i+1,lookup))
            return lookup[i]
```
### Key code insights
* recursive formula 

$$rob(i)=\left\{\begin{array} {rl} 0 & i\ge len(arr)\\ 
max(arr[i]+rob(i+2),rob(i+1)) & i < len(arr) \end{array} \right.$$
* base case
``` python
  if i>=len(nums):
            return 0
```