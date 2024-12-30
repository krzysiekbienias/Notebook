# Matrix multiplication
$$
C[i][j] = \sum_{k=1}^n A[i][k] \cdot B[k][j]
$$

```python
def matrix_multiplication(mat_a, mat_b):
    c = [[0] * len(mat_b[0]) for _ in range(len(mat_a))]
    for i in range(len(mat_a)):
        for j in range(len(mat_b[0])):
            for k in range(len(mat_a[0])):
                c[i][j] += mat_a[i][k] * mat_b[k][j]
    return c
```

### Key code insights
* we need 3 loops NOT 2
* ```C=[[0]*len(B) for _ in range(len(A))]``` prepare container for the result of multiplication.

A=2x3, B=3x4 then container must have 2 rows and 4 columns.. Please note that when we first create column in comprehension list this is why we have ```[0] * len(mat_b[0])```

