# GGSIPU – UNIT III ASSIGNMENT
Marks: 30 | Duration: 30 Minutes

## Instructions
- Answer only what is asked in 20–40 words or a short pseudocode/recurrence. [1]
- Provide core DP/BB formulations, not full code. [1]
- Clarity and correctness over length. [1]

## SECTION A – Short Theory [15 Marks]

1) DP essentials  
- List the three ingredients of DP and one-line purpose of each. [2][1]
  
       ANS= Input:
              Represents the data or information given to the problem.
              → Purpose: To define what the problem is based on and what needs to be processed.
              
           Processing:
              The operations or computations performed on the input.
              → Purpose: To transform the input into meaningful results through algorithms or logic.
              
          Output:
              The result produced after processing the input.
              → Purpose: To provide the final answer or decision to the given problem.

2) DP vs D&C  
- State two differences focusing on subproblem overlap and reuse; give one example for each. [2][1]

      ANS = Difference 1 – Subproblem Overlap:
          
          Dynamic Programming (DP): Solves problems where subproblems overlap, meaning the same subproblems occur multiple times.
          Example: Fibonacci series – the subproblem Fib(n-1) is reused in computing Fib(n).
          
          Divide and Conquer (D&C): Solves problems where subproblems are independent and do not overlap.
          Example: Merge Sort – each half of the array is sorted independently without reusing results.
          
          Difference 2 – Reuse of Results:
          
          Dynamic Programming (DP): Stores and reuses solutions to subproblems (using memoization or tabulation) to avoid recomputation.
          Example: Shortest path in a graph (e.g., Dijkstra’s algorithm).
          
          Divide and Conquer (D&C): Does not reuse results once a subproblem is solved; it combines them to form the final result.
          Example: Quick Sort – results of partitioned arrays are combined but not reused later.



3) Principle of optimality  
- Define it in one sentence and name any one problem satisfying it. [3][4]
        
      ANS = Principle of Optimality:
      It states that an optimal solution to a problem contains within it optimal solutions to its subproblems.
      Example:
      The Shortest Path Problem (e.g., Dijkstra’s or Bellman-Ford algorithm) satisfies the principle of optimality.

4) Memoization  
- Define memoization and contrast with tabulation in one line each. [1]

      ANS = Memoization: It is a top-down approach that stores results of solved subproblems using recursion to avoid recomputation.
      Tabulation: It is a bottom-up approach that solves all subproblems iteratively and stores results in a table.

5) Branch and Bound idea  
- Define BnB and the role of bounding in pruning in two lines. [5][6]

      ANS = Branch and Bound (BnB): It is a problem-solving technique that explores all possible solutions systematically while using bounds to eliminate unpromising branches.
      Bounding Role: The bound helps in pruning by discarding branches that cannot yield a better solution than the current best.

## SECTION B – Algorithms & Recurrences [15 Marks]

6) Matrix Chain Multiplication (A₁:5×4, A₂:4×6, A₃:6×2, A₄:2×7)  
a) Write m[i,j] recurrence and base case (no derivation). [4][7][8]  
b) State the minimum scalar multiplications (number only). [8][4]
      
       ANS = a)
          Recurrence Relation: 
                      m[i,j] = min_{i ≤ k < j} { m[i,k] + m[k+1,j] + p_{i-1} * p_k * p_j }
          b) Base Case:
                     m[i,i] = 0  for all i




## 7) Longest Common Subsequence (X = "ABCDGH", Y = "AEDFHR")

**a)** Write the LCS(i,j) recurrence and base. [1]  
**b)** Give the LCS length (number only). [1]

**Answer:**

**a)**  
LCS(i,j) =  
  0                 if i = 0 or j = 0  
  LCS(i−1,j−1) + 1  if X[i] = Y[j]  
  max(LCS(i−1,j), LCS(i,j−1)) if X[i] ≠ Y[j]

**b)**  
LCS length = **3**

---

## 8) Optimal Binary Search Tree  
(keys: 10, 20, 30; p = 0.4, 0.3, 0.3; assume q = 0)

**a)** Write w[i,j] and e[i,j] DP formulations with base. [1]  
**b)** State the minimum expected search cost (number only). [1]

**Answer:**

**a)**  
w[i,j] = w[i, j−1] + p[j]  
e[i,j] = min_{i ≤ r ≤ j} ( e[i, r−1] + e[r+1, j] + w[i,j] )

Base cases:  
w[i, i−1] = 0, e[i, i−1] = 0

**b)**  
Minimum expected search cost = **1.7**

---

## 9) 0/1 Knapsack – Branch & Bound  
(W = 5; w = {2,3,4,5}, p = {3,4,5,6})

**a)** Write the fractional upper bound formula used for pruning. [6][9][5]  
**b)** Show level-0 and level-1 nodes (include/exclude first item) with (v,w,ub) only. [5][6]

**Answer:**

**a)**  
Fractional Upper Bound Formula:  
ub = v + (W − w) × (next item’s p/w ratio)

**b)**  
- Level 0: (v = 0, w = 0, ub = 10.0)  
- Level 1 (Include item 1): (v = 3, w = 2, ub = 9.0)  
- Level 1 (Exclude item 1): (v = 0, w = 0, ub = 10.0)

---

## 10) Travelling Salesman Problem – Dynamic Programming (Held–Karp; 4 cities, example D given)

**a)** Write the C[S,j] recurrence and final answer expression. [1]  
**b)** Initialize base entries C[{k},k] for k = 2..4 (numbers only for the given D). [1]

**Answer:**

**a)**  
C[S, j] = min_{k ∈ S, k ≠ j} ( C[S − {j}, k] + D[k, j] )

Final answer:  
min_{j ≠ 1} ( C[{all cities}, j] + D[j, 1] )

**b)**  
C[{2},2] = D[1,2]  
C[{3},3] = D[1,3]  
C[{4},4] = D[1,4]

---


## Submission
- Submit `Unit3_Assignment_<YourName>.md` to GitHub Classroom; use fenced code blocks for recurrences/pseudocode. [10]

