# Tournament winner


| Id | Title          | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|----|----------------|------------|----------------|--------------|------------|-----------------|------------------|
| 1  | Two number sum | AlgoExpert | arrays         | Two pointers | easy       |

```python 
def tournament_winner(competitions, results):
    table=dict()
    for teams in competitions:
        for name in teams:
            table[name]=0
    for competition,outcome in zip(competitions,results):
        winner=get_winner(competition,outcome)
        table[winner]+=3
    league_winner=max(table,key=table.get)
    return league_winner

def get_winner(teams, result):
    if result ==0:
        return teams[1]
    else:
        return teams[0] 
```

### Key code insights

```python max(table,key=table.get) ``` wil return the key associated with the maximum value


# Move element to end.
https://www.algoexpert.io/questions/move-element-to-end

| Id | Title               | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|----|---------------------|------------|----------------|--------------|------------|-----------------|------------------|
| 4  | Move Element To End | AlgoExpert | array          | Two pointers | easy       |

```python
def moveElementToEnd(array, toMove):
    pointer=0
    for i in range(len(array)):
        if array[i]!=toMove:
            array[pointer],array[i]=array[i],array[pointer]
            pointer+=1
    return array
```

# First duplicated value
| Title                 | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|-----------------------|------------|----------------|--------------|------------|-----------------|------------------|
| First Duplicate Value | AlgoExpert | array          | hash set     | easy       | O(n)            | O(n)             |


```python
def firstDuplicateValue(array):
    seen=set()
    for num in array:
        if num in seen:
            return num
        else:
            seen.add(num)
    return -1
```

### Key code insights
* Alternative approach would be with hash map but the solution above seems to be more elegant

# Containers With Most Water.

| Title                       | Source   | Data Structure | Algo Concept         | Difficulty | Time Complexity | Space Complexity |
|-----------------------------|----------|----------------|----------------------|------------|-----------------|------------------|
| Containers With Most Water. | LeetCode | array          | Two pointers, greedy | Medium     |

!['alt text'](../captures/water_container.png)

* Input: ```height = [1,8,6,2,5,4,8,3,7]```
* Output: $49$
* Explanation: The above vertical lines are represented by array ```[1,8,6,2,5,4,8,3,7]```. In this case, the max area of water (blue section) the container can contain is $49$.

```python
def maxArea(self, height: List[int]) -> int:
        left=0
        right=len(height)-1
        max_area=0
        width=right-left
        while left<right:
            max_area=max(max_area,min(height[left],height[right])*width)
            if height[left]<=height[right]:
                left+=1
                width-=1
            else:
                right-=1
                width-=1
        return max_area 
```
### Key code insights
* we start from both sides.

* The reason for taking the minimum is that the area of water that can be trapped between the two lines is limited by the shorter of the two lines. The taller line won’t affect the maximum area because the shorter one is the limiting factor in determining how much water can be held.
* ```width-=1```each iteration narrow container 

# High five
https://leetcode.com/problems/high-five/description/?envType=company&envId=goldman-sachs&favoriteSlug=goldman-sachs-thirty-days

recently asked in Goldman Sachs
| Title     | Source   | Data Structure | Algo Concept                    | Difficulty | Time Complexity | Space Complexity |
|-----------|----------|----------------|---------------------------------|------------|-----------------|------------------|
| High Five | LeetCode | Array/dict     | Create dictionary from 2D array | easy       | O(nlogk)        | O(n)             |

Regarding time complexity k is the average number of scores per ID, m is unique Ids, n total number of scores. The dominant term depends on  n  and  m :
* In most cases,  $m \ll n$ , so  $O(n \log k)$  dominates.
```python 
def top_five_average(marks, threshold=5):
    return sum(marks[:threshold]) // threshold

def high_five(items: List[List[int]]) -> List[List[int]]:
    performance_dict = {}
    results=[]
    for item in items:
        if item[0] not in performance_dict:
            performance_dict[item[0]] = [item[1]]
        else:
            performance_dict[item[0]].append(item[1])
    for key in performance_dict:
        performance_dict[key].sort(reverse=True)
        results.append([key,top_five_average(performance_dict[key])])
    results_sorted=sorted(results,key=lambda x:x[0])
    return results_sorted
```


# Smallest difference (AlgoExpert)
```python
def smallest_difference(arrayOne, arrayTwo):
    arrayOne.sort()
    arrayTwo.sort()
    i, j = 0, 0
    min_diff = float('inf')
    closest_pair = []
    while i < len(arrayOne) and j < len(arrayTwo):
        current_diff = abs(arrayOne[i] - arrayTwo[j])
        if current_diff == 0:
            return [arrayOne[i], arrayTwo[j]]
        min_diff = min(min_diff, current_diff)
        if current_diff <= min_diff:  # update closest pair only if differnece is smaller
            closest_pair = [arrayOne[i], arrayTwo[j]]
        if arrayOne[i] < arrayTwo[j]:
            i += 1
        else:
            j += 1
    return closest_pair
```

# Non Constructible Change
```python
def non_constructible_change(coins):
    coins.sort()
    if not coins:
        return 1
    current_change = 0
    for coin in coins:
        if coin > current_change:
            return current_change + 1
        current_change += coin
    return current_change + 1
```

# Minimum loss
| Title        | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity        | Space Complexity |
|--------------|------------|----------------|--------------|------------|------------------------|------------------|
| MInimum Loss | Haker Rank | array          | greedy       | medium     | O(n log n) sort price  | O(n) dictionary  |
The minimum_loss function computes the smallest possible financial loss when buying and selling a property, given an array of property prices. The function ensures that the buy date occurs before the sell date in the original sequence of prices.
## Key Idea
The algorithm leverages sorting to efficiently compare prices and their order while maintaining the relationship between the original and sorted indices using a dictionary. This ensures valid transactions (buy before sell) and helps identify the minimum loss.
## Algorithm
1.	Create a Mapping Between Prices and Their Indices:
    *	A dictionary di is created where:
	    - Key: The price.
		- Value: The index of the price in the original array.
	* This mapping allows efficient lookups to validate the order of transactions after sorting.
  ```python
prices = [20, 7, 8, 2, 5]
di = {20: 0, 7: 1, 8: 2, 2: 3, 5: 4}
```
2. Sort price

The prices array is sorted in ascending order. This allows the algorithm to easily compare consecutive prices to compute 
losses.

3.	Iterate Over Sorted Prices to Compute Minimum Loss:
* Loop through the sorted prices and calculate the loss for every consecutive pair:
	```loss = prices[i] - prices[i - 1].```

* Check if the buy date occurs before the sell date using the di dictionary:
```If di[prices[i - 1]] > di[prices[i]]```, then it is a valid transaction.
```python
For sorted_prices = [2, 5, 7, 8, 20]:
Pair (5, 2): Valid, Loss = 5 - 2 = 3
Pair (7, 5): Invalid, skip.
Pair (8, 7): Invalid, skip.
Pair (20, 8): Valid, Loss = 20 - 8 = 12
```
4.	Update Minimum Loss:
* Keep track of the smallest valid loss encountered during the iteration.
5.	Return Result:
*	After completing the iteration, return the minimum loss.
## Asumptions
* All prices are unique
* The transaction is valid only if the buy date occurs before the sell date in the original sequence.

# Subarray Sort
| Title         | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|---------------|------------|----------------|--------------|------------|-----------------|------------------|
| Subarray Sort | AlgoExpert | array          | Two pointers | medium     | O(n)            | O(1)             |

The subarray_sort function identifies the smallest contiguous subarray that, if sorted, would make the entire array sorted. The function efficiently determines the boundaries of this subarray by leveraging a combination of linear scans and boundary expansion.
## Algorithm
How the Algorithm Works
1.	Check if the Array Is Already Sorted:
	* If the array is already sorted, return ```[-1, -1]```.
	* This is achieved by comparing the input array with its sorted version using sorted(array).
2.	Find the Left Boundary (l):
	* Starting from the left of the array, find the first index l where the order is broken:
        * The order is broken if ```array[l] > array[l + 1]```.
3.	Find the Right Boundary (r):
	*	Starting from the right of the array, find the first index r where the order is broken:
	        *	The order is broken if ```array[r] < array[r - 1]```.
4.	Identify the Minimum and Maximum of the Unsorted Subarray:
	*	Compute the minimum (subarray_min) and maximum (subarray_max) values within the identified subarray ```(array[l:r + 1])```.
5.	Expand the Boundaries if Necessary:
	*	Expand the left boundary (l) by moving it to the left until all elements before it are smaller than subarray_min.
	*	Expand the right boundary (r) by moving it to the right until all elements after it are greater than subarray_max.
6.	Return the Result:
	*	Return the indices ```[l, r]``` that represent the smallest subarray that needs to be sorted.

```python
def subarray_sort(array):
    if sorted(array) == array:
        return [-1, -1]
    n = len(array)
    l = 0
    r = n - 1
    # 1. looking for index from left where order is broken
    while l < n and array[l] <= array[l + 1]:
        l += 1
    # 2. looking for index from right where order is broken.
    # Note that r is bounded from zero because we are going from
    while r > 0 and array[r] >= array[r - 1]:
        r -= 1
    # 3. find min and max in the unsorted subarray
    subarray_min = min(array[l:r + 1])
    subarray_max = max(array[l:r + 1])
    # 4. Expand the right boundary if needed pointers go to opposite direction
    while l > 0 and array[l - 1] > subarray_min:
        l -= 1
    while r < n - 1 and array[r + 1] < subarray_max:
        r += 1
    return [l, r]
```

# Smallest difference
| Title               | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|---------------------|------------|----------------|--------------|------------|-----------------|------------------|
| Smallest Difference | AlgoExpert | array          | Two pointers | medium     | O(n)            | O(1)             |

```python
def smallest_difference(array_one, array_two):
    array_one.sort()
    array_two.sort()
    i, j = 0, 0
    min_diff = float('inf')
    closest_pair = []
    while i < len(array_one) and j < len(array_two):
        current_diff = abs(array_one[i] - array_two[j])
        if current_diff == 0:
            return [array_one[i], array_two[j]]
        min_diff = min(min_diff, current_diff)
        if current_diff <= min_diff:  # update closest pair only if differnece is smaller
            closest_pair = [array_one[i], array_two[j]]
        if array_one[i] < array_two[j]:
            i += 1
        else:
            j += 1
    return closest_pair
```

# Missing numbers
| Title           | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|-----------------|------------|----------------|--------------|------------|-----------------|------------------|
| Missing Numbers | AlgoExpert | arrayz`          | hash set     | medium     | O(n)            | O(n)             |
## Description 
The missing_numbers function identifies two missing integers from an unordered list of unique integers, where the integers are within the range [1, n]. The function efficiently finds the missing numbers using a set-based approach to check for their absence.

## Algotithm
How the Algorithm Works
1.	Identify the Scope of Numbers:
*	The given list nums contains n - 2 unique integers, where the full range of integers is [1, n].
*	Since two numbers are missing, the range of numbers to consider is [1, len(nums) + 2].
2.	Use a Set for Fast Lookup:
*	Convert the input array nums into a set called numbers_in_scope. This allows for O(1) time complexity when checking if a number is present.
3.	Iterate Through the Full Range:
*	Iterate over all numbers in the range [1, len(nums) + 2]:
    *	If a number is not present in numbers_in_scope, add it to the result list.
4.	Return the Result:
*	Once the iteration is complete, return the result list containing the two missing numbers.

## Alternative solutions
1. Bitwise 
2. Mathematical formulas

```python
def missing_numbers(nums):
    result=[]
    numbers_in_scope=set(nums)
    for num in range(1,len(nums)+3):
        if num not in numbers_in_scope:
            result.append(num)
    return result
```



# Coun

