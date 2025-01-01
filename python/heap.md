# Kth Largest Element in an Array
```python 
def find_kth_largest_element(arr, k):
    heap=arr[:k]
    heapq.heapify(heap)
    for num in arr[k:]: #first 2 elements from array is already in heap and has been heapify
        if num>heap[0]:
            heapq.heappushpop(heap, num)
    return heap[0] # that would be the Kth largest element
```

### Key code insights
* To find the k-th largest element, we don’t need to sort the entire array (which would be inefficient for large arrays). Instead, we only need to keep track of the k largest elements we’ve seen so far.
* It allows us to efficiently manage the smallest element of the k largest elements we’ve found so far.
* Time Complexity:
	- Building the heap initially with the first k elements takes O(k).
	 - For each subsequent element, inserting into the heap (which maintains size k) takes O(\log k).
	 - Therefore, processing all n elements takes $O(n \log k)$ time, which is much more efficient than sorting the entire array, which would take $O(n \log n)$.
* Space Complexity
  $O(k)$ because we need only store k elements in heap

# Find Three Largest Numbers
Almost identical like Kth Largest Element in an Array. It was in AlgoExpert dedicated to searching so try also using this method

```python
def find_three_largest_numbers(array):
    heap = array[:3]
    heapq.heapify(heap)
    for num in array[3:]:  # first 2 elements from array is already in heap and has been heapify
        if num > heap[0]:
            heapq.heappushpop(heap, num)
    heap.sort()
    return heap
```