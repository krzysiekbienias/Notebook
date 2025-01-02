# Minimum Waiting Time
## Problem statement

It is important to understand problem correctly.

Definition: The sum of the waiting times for all tasks/queries. This excludes the execution time of each task itself and focuses only on how long tasks are idle before they start.

$\text{Waiting Time} = \sum (\text{Waiting Time of Each Task})$

where the waiting time for a task depends on how long the earlier tasks take.

a slightly different is minimum total time.

1. Minimum Total Time
	* Definition: The sum of the completion times for all tasks/queries. This includes:
	*	The time each task spends waiting to start (waiting time).
	*	The time it takes to execute each task (execution time).

2. Formula:

$\text{Total Time} = \sum (\text{Completion Time of Each Task})$

where Completion Time includes both waiting and execution times.

Example: $[3, 2, 1, 2, 6]$
1.	Sorted Array: [1, 2, 2, 3, 6].
2.	Total Time Calculation:
	*	Completion Times:
	*	Query 1: Completes at 1.
	*	Query 2: Completes at 1 + 2 = 3.
	*	Query 3: Completes at 3 + 2 = 5.
	*	Query 4: Completes at 5 + 3 = 8.
	*	Query 5: Completes at 8 + 6 = 14.
	*	Total Time = 1 + 3 + 5 + 8 + 14 = 31.
3.	Waiting Time Calculation:
	*	Waiting Times:
	*	Query 1: 0.
	*	Query 2: 1.
	*	Query 3: 1 + 2 = 3.
	*	Query 4: 1 + 2 + 2 = 5.
	*	Query 5: 1 + 2 + 2 + 3 = 8.
	*	Total Waiting Time = 0 + 1 + 3 + 5 + 8 = 17.

Summary of the Difference:
 * Minimum Total Time:
 * 	Includes both waiting and execution times.
 *	Result: 31 in this case.
 *	Minimum Waiting Time:
 *	Focuses only on how long tasks wait before starting.
 *	Result: 17 in this case.

The two metrics are closely related but not equivalent because one includes execution time while the other does not.

## Key Insight
The first step is to sort the queries in ascending order so that we start with the shortest query.

## Why use Greedy Algorithm?
A greedy algorithm is well-suited to this problem because it follows the strategy of making the locally optimal choice at each step with the hope that these choices lead to a globally optimal solution. 

4. Summary of the Difference:
* Minimum Total Time:
    - Includes both waiting and execution times.
    - Result: 31 in this case.
* Minimum Waiting Time:
   - Focuses only on how long tasks wait (are in idle state) before starting.
   - Result: 17 in this case.

```python
def minimum_waiting_time(queries):
    # minimum_waiting_time only considers the time queries spend waiting before they start execution.

    # Sort the list of queries in ascending order
    queries.sort()

    # Initialize total waiting time
    total_waiting_time = 0

    # Initialize accumulated waiting time for each query
    accumulated_waiting = 0

    # Loop through the queries, skipping the last one as it does not contribute to waiting time
    for i in range(len(queries) - 1):
        # Increase accumulated waiting by the duration of the current query
        accumulated_waiting += queries[i]

        # Add the current accumulated waiting to the total waiting time
        total_waiting_time += accumulated_waiting

    return total_waiting_time
```

# Class Photos
| Title        | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|--------------|------------|----------------|--------------|------------|-----------------|------------------|
| Class Photos | AlgoExpert | array          | greedy       | easy       | O(n log n)      | O(1)             |
```python
def class_photos(red_shirt_heights, blue_shirt_heights):
    red_shirt_heights.sort()
    blue_shirt_heights.sort()
    # we need to determine which group will be in front based on height of the shortest person.
    if red_shirt_heights[0] < blue_shirt_heights[0]:
        for red, blue in zip(red_shirt_heights, blue_shirt_heights):
            if red >= blue:
                return False
    else:
        for red, blue in zip(red_shirt_heights, blue_shirt_heights):
            if blue >= red:
                return False

    return True
```


### Key insight
The key insight is that the problem has a structure where making the locally optimal choice (placing the smallest group in the front and ensuring each corresponding row satisfies the condition) leads to the globally optimal solution. Sorting guarantees that no better arrangement exists than the one derived from this greedy approach:
* The algorithm determines which t-shirt group (red or blue) should be in front based on a single decision: comparing the smallest student in each group
* Comparing heights row by row ensures that once a t-shirt group is assigned to the front or back, the condition will hold for the entire group.
* Once this decision is made, the algorithm enforces the chosen ordering (red in front or blue in front) throughout the entire arrangement.
* If any pair violates the condition (```red >= blue or blue >= red```, depending on the arrangement), the algorithm immediately concludes that the arrangement is not feasible.
* This step-by-step validation ensures that the algorithm doesn’t backtrack or revisit previous decisions—it either succeeds or fails in a single pass.
* Time complexity $O(n \log n)$ because of sorting.
* Space complexity $O(1)$

# Best time to buy and sell equity
## How to classify this challenge?

Summary table:

| Variant                | Classification      | Reason                                                                    |
|------------------------|---------------------|---------------------------------------------------------------------------|
| Single Transaction     | Greedy              | Local decisions (min price, max profit) with no overlapping subproblems.  |
| Unlimited Transactions | Greedy              | Each upward trend is independent; add local profits.                      |
| k Transactions         | Dynamic Programming | Overlapping subproblems require combining previous transaction states.    |
| Cooldown/Fees          | Dynamic Programming | State depends on multiple variables (e.g., cooldown or transaction fees). |

## Variant 1 Single transaction. 
```python
def best_time_to_buy_and_sell(prices:List[int]):
    if not prices:
        return 0 # Handle empty list case
    min_price=float("inf")
    max_profit=0
    
    for price in prices:
        # Update the minimum price seen so far
        min_price = min(min_price, price)
        #calulate profit if sold at the current price
        profit=price - min_price
        #update the maximum profit
        max_profit = max(max_profit, profit)
    return max_profit
```

## Variant 2 Multiple transactions
##  Assumptions:
* You can buy nd sell the stock multiple times.
* You cannot hold more than one stock at time.
* We want to maximize the total profit.
### Key insight:
* Buy low sell hight repeatedly.
```python

```