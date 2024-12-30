# Nth Fibonacci
https://www.algoexpert.io/questions/nth-fibonacci

```python
def getNthFib(n, lookup=None):
    lookup ={} if lookup is None else lookup
    if n in lookup:
        return lookup[n]
    if n==0:
        return 0
    elif n==1:
        return 0
    elif n==2:
        return 1
    else:
        lookup[n]=getNthFib(n-1,lookup)+getNthFib(n-2,lookup)
        return lookup[n]
```
### Key code insights
```lookup ={} if lookup is None else lookup``` how to handle with memoization


# Greatest common divisor

``` python
def greatest_common_divisor(n: int, m: int) -> int:
    """
    Description
    -----------
    Function returns greatest common divisor of n and m. It utilizes Euclidean algorithm,

    Parameters
    ----------
    n:int
    m:int

    Returns
    -------
    int

    """
    if m == 0:
        return n
    else:
        return greatest_common_divisor(m, n % m)
```

# Sum of digits

```python
def sum_of_digits(n: int) -> int:
    if n == 0:
        return 0
    else:
        return n % 10 + sum_of_digits(n // 10)
```
