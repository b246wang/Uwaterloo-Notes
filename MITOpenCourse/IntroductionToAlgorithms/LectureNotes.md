# Lecture 1
### Algorithms & 3 concerns
- **_Efficient_** procedures for solving large scale problems
- **_Scalability_**: able to solve the growth of the data
- **_Classic data structures_**: balanced BST, Hash tables...

---
### 1D Peak Finder: Find a peak if exists
- Given an array A, position A[i] is a peak if and only if A[i] >= A[i-1] and A[i] >= A[i+1]
- Edge: A[0] is a peak iff A[0] >= A[1]
- Based on this definition, there always exists a peak in any given non-empty array

##### θ(n) solution: A traversal of the array
- In worst case, you have to look at all n elements

##### Divide and Conquer solution:
1. look at the middle of the array A[n/2]
2. if A[n/2] < A[n/2-1], only look for a peak in left half 0 ... n/2-1
  * since left side is bigger, there will be a peak to the left
3. elseif A[n/2] < A[n/2+1], only look at right half of the array n/2+1 ... n
  * vice versa
4. else A[n/2] is the peak

```
COMPLEXITY:
T(n) = T(n/2) + θ(1)
Base case: T(1) = θ(1)
Expand: T(n) = θ(1) + θ(1) + ... + θ(1)
There are log2(n) times of θ(1) => θ(log2(n))
```

### 2D Version:
|        | c          |   |
--- | --- | ---
| b |a| d|
|  | e| |
- n rows, m columns
- a is a 2D-peak if a>=b, a>=c, a>=d, a>=e

##### Greedy Ascent Algorithm
- Move to the larger number adjacent to current one
- θ(mn) complexity
- θ(n^2) if m = n

