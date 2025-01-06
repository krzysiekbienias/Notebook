# Bubble sort
1. outer loop start from end 
2. inner loop upper bound will be outer loop
This would improve the algorithm a little and we will avoid performing some redundant operations.

this is basic version
```python
def bubble_sort(arr: List[int]) -> List[int]:
    for u in range(len(arr)-1, 0, -1):
        for i in range(u):
            if arr[i] > arr[i+1]:
                arr[i], arr[i+1] = arr[i+1], arr[i]
```

We can also introduce a boolean variable "changed" to check if we have changed the array when going through it in our inner loop. 

```python
def bubble_sort(arr: List[int]) -> List[int]:
    for u in range(len(arr)-1, 0, -1):
        changed=False
        for i in range(u):
            if arr[i] > arr[i+1]:
                arr[i], arr[i+1] = arr[i+1], arr[i]
                changed =True
        if not changed:
            break
```
### Key code insights
``` if not changed:``` this condition checked if any changes were made in inner lopp if not we can break the lopp and stop the algorithm.


# Insertion sort
```python
def insertion_sorting(array):
    #cards analogy
    for i in range(1, len(array)):
        j = i
        while j > 0 and array[j] < array[j - 1]:
            array[j], array[j - 1] = array[j - 1], array[j]
            j -= 1
    return array
```
It is highly efficient way of sorting if we know that only few items are not in correct place

# Merge sort 
```python
def merge(left_array: List[int], right_array: List[int]) -> List[int]:
    """
    Description
    Merge two sorted arrays into a new sorted array.
    Parameters
    ----------
    left_array
    right_array

    Returns
    -------

    """
    l, r, res = 0, 0, []
    while l < len(left_array) or r < len(right_array):
        al = left_array[l] if l < len(left_array) else float('inf')
        br = right_array[r] if r < len(right_array) else float('inf')
        if al < br:
            res.append(al)
            l += 1
        else:
            res.append(br)
            r += 1
    return res
```
```python
def merge_sort(array: List[int]) -> List[int]:
    """
    Description
    -----------
    Merge two sorted arrays into a new sorted array.
    Parameters
    ----------
    array

    Returns
    -------

    """
    if len(array) <= 1:
        return array
    l = merge_sort(array[:len(array) // 2])
    r = merge_sort(array[len(array) // 2:])
    return merge(l, r)
```


## Count Inversions