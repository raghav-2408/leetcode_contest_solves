## Matrix Similarity After Cyclic Shifts

`code`
```python
# a = [[1,2,1,2],[5,5,5,5],[6,3,6,3]]
class Solution:
    def areSimilar(self, mat: List[List[int]], k: int) -> bool:
        m = len(mat) # 3
        n = len(mat[0])# first matrix
        copy = [i[:] for i in mat]
        for i in range(m):
            if i%2==1: # odd
                mat[i] = mat[i][-k%n:]+mat[i][:-k%n] 
                # [-k%n] -> reverses / performs the right shifting / interchanges
            else:
                mat[i] = mat[i][k%n:]+mat[i][:k%n]
        return mat == copy

'''
 consider this as an example 
[[1,2,1,2], -> copy
 [5,5,5,5],
 [6,3,6,3]]

 after interchanging
 [[2,1,2,1],
 [5,5,5,5],
 [3,6,3,6]]

perform right shift again (mat)
 [[1,2,1,2],
 [5,5,5,5],
 [6,3,6,3]]

 copy==mat -> true
'''
```
```Output```
```
true 
```