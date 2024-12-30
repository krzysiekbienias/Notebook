# Is Prime

```python
def is_prime(n: int) -> bool:
    """
    Description
    -----------
    Checks if a number is prime or not.
    Parameters
    ----------
    n

    Returns
    -------

    """
    if n <= 1:
        return False
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True

```
When checking if a number  n  is prime, you can stop the loop at   $\lfloor \sqrt{n} \rfloor + 1$    because of the mathematical properties of factors:

* Every number  n  can be expressed as a product of two factors:  $a \times b = n $.
* If both  $a$  and  $b$  were greater than  $\sqrt{n}$ , their product  $a \times b$  would exceed  $n$ , which is a contradiction.
  

What is conclusion?
* If no factors are found up to  $\sqrt{n}$ , there won’t be any factors greater than  $\sqrt{n}$  either.

### Note
You cannot stop on $\lfloor \sqrt{n} \rfloor$. Contrexample $n=49$.If your loop checks divisors only up to  6  (strictly less than  \sqrt{49} ), it will miss  7 , which is a factor of  49 . 

# Perfect number
| Title          | Source   | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|----------------|----------|----------------|--------------|------------|-----------------|------------------|
| Perfect Number | LeetCode | Math           | Math         | easy       | ?               | ?                |
### def
A perfect number is a positive integer that is equal to the sum of its positive divisors, excluding the number itself. A divisor of an integer x is an integer that can divide x evenly.

$28$ is a perfect number because $28=1+2+4+7+14$ 

```python
def all_divisors_with_sqrt(number): #more optimal solution without last divisor.
        l_divisors=[]
        for i in range(2,int(number**0.5)+1):
            if number % i==0:
                l_divisors.append(i)
                l_divisors.append(int(number/i))
        return [1]+l_divisors

 def checkPerfectNumber(num: int) -> bool:
        if num <0:
            return False
        if num ==1:
            return False
        int_divisorsSum=sum(all_divisors_with_sqrt(number=num))
        if int_divisorsSum==num:
            return True
        else:
            return False
```

