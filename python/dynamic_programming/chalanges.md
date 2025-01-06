# House Robber
The ```rob``` function solves the House Robber Problem, where you must maximize the amount of money robbed from a row of houses without robbing two adjacent houses. The problem is solved using dynamic programming with memoization to ensure optimal performance.
| Title        | Source   | Data Structure | Algo Concept                   | Difficulty | Time Complexity | Space Complexity |
|--------------|----------|----------------|--------------------------------|------------|-----------------|------------------|
| House Robber | leetcode | array          | Dynamic programming /recursion | Medium     |complete

* Input: ```nums = [2,7,9,3,1]```
* Output: 12
* Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
    
    Total amount you can rob = 2 + 9 + 1 = 12.
## Algorithm

1.	Recursive Exploration:
	*	The function __explores__ two options for each house:
    	   - Rob the current house and skip the next (nums[i] + rob(nums, i+2)).
	       - Skip the current house and consider the next (rob(nums, i+1)).
2.	Base Case:
	* If the index i is beyond the last house ```(i >= len(nums))```, no money can be robbed, so the function returns 0.
3.	Memoization:
	*	The function uses a dictionary lookup to store previously computed results for each index i. This avoids redundant calculations and improves efficiency.
4.	Decision Making:
	*	For each house at index ```i```, the maximum amount that can be robbed is stored as:
```python
lookup[i]=max(nums[i]+self.rob(nums,i+2,lookup),self.rob(nums,i+1,lookup))
```

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
* memization happen by means of:
  ```python 
  lookup={} if lookup is None else lookup
  ```


# Water Area
The water_area function calculates the total amount of water trapped between bars of varying heights after rainfall. It uses a two-pointer approach to efficiently compute the water trapped in O(n) time, making it both space- and time-efficient.

## Algorithm
The algorithm iterates through the array of heights using two pointers (left and right) to dynamically calculate the trapped water:
1.	Initialization:
	*	Set two pointers: left at the start of the array and right at the end.
	*	Track the maximum heights seen so far: left_max and right_max.
	*	Initialize max_area to store the total trapped water.
2.	Two-Pointer Traversal:
	*	While left is less than right:
        - Compare the heights at the left and right pointers.
	    - Move the pointer with the smaller height inward, updating the trapped water based on the difference between the current height and the corresponding maximum height (left_max or right_max).
		- Update left_max or right_max as necessary.
3.	Water Trapping Logic:
	*	If the height at the left pointer is smaller:
    	- If it is greater than or equal to left_max, update left_max.
  	    - Otherwise, add left_max - heights[left] to max_area.
	    -	Increment left.
	*	If the height at the right pointer is smaller or equal:
	    -	If it is greater than or equal to right_max, update right_max.
	    -	Otherwise, add right_max - heights[right] to max_area.
	    -	Decrement right.
## Why it is dynamic programming?
Try to thing about it.

```python
def water_area(heights: List[int]) -> int:
    if len(heights) < 3:
        return 0
    left, right = 0, len(heights) - 1
    left_max, right_max = 0, 0
    max_area = 0
    while left < right:
        if heights[left] < heights[right]:
            if heights[left] >= left_max:
                left_max = heights[left]

            else:
                max_area += left_max - heights[left]
            left += 1
        else:
            if heights[right] >= right_max:
                right_max = heights[right]

            else:
                max_area += right_max - heights[right]
            right -= 1
    return max_area
```

