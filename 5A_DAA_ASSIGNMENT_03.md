# 🧠 GGSIPU – UNIT III ASSIGNMENT  
**Subject:** Design and Analysis of Algorithms (DAA)  
**Marks:** 30 | **Duration:** 30 Minutes  
**Name:** <YourName>  
**File:** `Unit3_Assignment_<YourName>.md`  

---

## 📝 Instructions  
- Answer concisely in **20–40 words** or short **pseudocode/recurrence**.  
- Provide **core DP/BB formulations** only (no derivation/code).  
- **Clarity and correctness** > length.  

---

## ✳️ SECTION A – Short Theory (15 Marks)

### **1) DP Essentials**  
**Three ingredients of Dynamic Programming:**  
| Ingredient | Purpose |
|-------------|----------|
| **Optimal Substructure** | Problem can be broken into smaller optimal subproblems. |
| **Overlapping Subproblems** | Same subproblems are solved multiple times. |
| **Memoization/Tabulation** | Store subproblem results to avoid recomputation. |

---

### **2) DP vs Divide & Conquer**

| Feature | Dynamic Programming | Divide & Conquer |
|----------|---------------------|------------------|
| **Subproblem Overlap** | Subproblems overlap and are reused. | Subproblems are independent. |
| **Reuse Mechanism** | Results stored and reused (memoization). | No reuse of computed results. |
| **Example** | Fibonacci Series, LCS | Merge Sort, Quick Sort |

---

### **3) Principle of Optimality**  
> *A problem satisfies the principle of optimality if its optimal solution can be constructed from optimal solutions of its subproblems.*  
**Example:** Shortest Path Problem (e.g., Floyd–Warshall, Bellman–Ford).

---

### **4) Memoization vs Tabulation**

| Term | Definition |
|-------|-------------|
| **Memoization** | Top-down DP approach storing results of recursive calls. |
| **Tabulation** | Bottom-up iterative DP filling a table from base cases. |

---

### **5) Branch and Bound Idea**  
> *Branch and Bound systematically explores the solution space by branching on decisions and bounding infeasible or non-promising nodes.*  
**Bounding** helps **prune** branches that cannot lead to better solutions, improving efficiency.

---

## ⚙️ SECTION B – Algorithms & Recurrences (15 Marks)

### **6) Matrix Chain Multiplication**

Given:  
A₁: 5×4, A₂: 4×6, A₃: 6×2, A₄: 2×7  

#### (a) Recurrence and Base  
```text
Base: m[i,i] = 0
Recurrence: m[i,j] = min_{i ≤ k < j} ( m[i,k] + m[k+1,j] + p_{i-1} * p_k * p_j )
```

#### (b) Minimum Scalar Multiplications  
**= 158**

---

### **7) Longest Common Subsequence (LCS)**  
Given: X = "ABCDGH", Y = "AEDFHR"

#### (a) Recurrence and Base  
```text
Base: LCS(i,0) = 0, LCS(0,j) = 0
Recurrence:
LCS(i,j) = 1 + LCS(i-1,j-1) if X[i]==Y[j]
          = max(LCS(i-1,j), LCS(i,j-1)) otherwise
```

#### (b) LCS Length  
**= 3**  → (“ADH”)

---

### **8) Optimal Binary Search Tree**

Keys: {10, 20, 30}  
Probabilities p = {0.4, 0.3, 0.3}, assume q = 0  

#### (a) DP Formulations  
```text
Base: e[i,i-1] = 0, w[i,i-1] = 0
Recurrence:
w[i,j] = w[i,j-1] + p[j]
e[i,j] = min_{i ≤ r ≤ j} ( e[i,r-1] + e[r+1,j] + w[i,j] )
```

#### (b) Minimum Expected Search Cost  
**= 1.7**

---

### **9) 0/1 Knapsack – Branch and Bound**

Given:  
W = 5;  
w = {2, 3, 4, 5};  
p = {3, 4, 5, 6}

#### (a) Fractional Upper Bound Formula  
```text
UB = v + (W - w) * (p_i / w_i)  // using next item fractionally
```

#### (b) Level Nodes  
| Level | Items Included | (v, w, ub) |
|--------|----------------|------------|
| 0 | {} | (0, 0, 9.0) |
| 1 | {1 included} | (3, 2, 9.0) |
| 1 | {1 excluded} | (0, 0, 8.0) |

---

### **10) Travelling Salesman Problem (TSP – Held–Karp)**

#### (a) Recurrence and Final Expression  
```text
Base: C[{1},1] = 0
Recurrence:
C[S, j] = min_{k ∈ S, k ≠ j} [ C[S - {j}, k] + D[k][j] ]
Final: min_{j ≠ 1} [ C[{all cities}, j] + D[j][1] ]
```

#### (b) Base Entries (for k = 2..4)  
If D is given (example):  
D =
|   | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| 1 | 0 | 10 | 15 | 20 |
| 2 | 10 | 0 | 35 | 25 |
| 3 | 15 | 35 | 0 | 30 |
| 4 | 20 | 25 | 30 | 0 |

Then:
```
C[{2},2]=10  
C[{3},3]=15  
C[{4},4]=20
```

---

## 📘 Summary Table

| Problem | Key Idea | Base | Recurrence / Formula |
|----------|-----------|------|----------------------|
| MCM | DP with partitioning | m[i,i]=0 | m[i,j]=min(m[i,k]+m[k+1,j]+cost) |
| LCS | DP on strings | LCS(i,0)=0 | if match→+1 else max |
| OBST | Probabilistic DP | e[i,i-1]=0 | e[i,j]=min(e[i,r-1]+e[r+1,j]+w[i,j]) |
| Knapsack (BnB) | Pruning via UB | Level 0 root | UB=v+(W−w)*(p/w) |
| TSP | Subset DP | C[{k},k]=D[1][k] | C[S,j]=min(C[S−{j},k]+D[k][j]) |

---

## 📊 Diagram References

### Dynamic Programming Flow
```
Problem
 ├── Divide into Subproblems
 ├── Solve Subproblems
 ├── Store Results (Memoization/Tabulation)
 └── Combine for Optimal Solution
```

### Branch and Bound Tree (Knapsack Example)
```
        (0,0,9.0)
        /        \
   (3,2,9.0)   (0,0,8.0)
```

---

**✅ End of Assignment**  
> *Prepared for submission to GitHub Classroom as `Unit3_Assignment_<YourName>.md`*  
