# Palindrome check

| Title            | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|------------------|------------|----------------|--------------|------------|-----------------|------------------|
| Palindrome check | AlgoExpert | string         | Two pointers | easy       | O(n)            | O(1)             |
```python
def isPalindrome(string):
    l_p=0
    r_p=len(string)-1
    while l_p<r_p:
        if string[l_p]==string[r_p]:
            l_p+=1
            r_p-=1
        else:
            return False
    return True
```
### Key code insights
* two pointers, and while loop.