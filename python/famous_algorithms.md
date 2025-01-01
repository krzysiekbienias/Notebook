# Kadane's Algorithm

| Title               | Source     | Data Structure | Algo Concept        | Difficulty | Time Complexity | Space Complexity |
|---------------------|------------|----------------|---------------------|------------|-----------------|------------------|
| Kathane’s Algorithm | AlgoExpert | array          | dynamic programming | easy       | O(n)            | O(1)             |

```python
def kadanes_algorithms(array: List[int]) -> List[int]:
    max_sum = -float("inf")
    current_sum = 0
    for num in array:
        current_sum += num
        max_sum = max(current_sum, max_sum)
        if current_sum < 0:
            current_sum = 0
    return max_sum

```
### Key points.
* It is NOT about two pointers
* ```max_sum``` is initialized to a very small value ```(-float('inf'))``` to handle cases where all array elements are negative.
* The algorithm tracks the maximum subarray sum (max_sum) encountered so far.
* Kadane’s Algorithm can be applied in several financial scenarios, especially those involving optimization problems where the goal is to maximize a contiguous segment of data. Here are some practical use cases in finance:
  - Maximizing Profit from Stock Price Changes
    - Problem: Find the maximum profit you can achieve by buying and selling a stock once, given daily price changes.
  - Analyzing Profitability of a Trading Strategy
    - Problem: Given daily profits and losses from a trading strategy, determine the most profitable consecutive trading period.