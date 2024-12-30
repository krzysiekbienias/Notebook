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