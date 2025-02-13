# LEETCODE-Queues-3066
---

### **Code Analysis**
The function aims to make all elements in the array **at least** `k` by repeatedly:
1. Extracting the **two smallest** numbers.
2. Merging them using the formula:  
   \[
   z = \min(x, y) \times 2 + \max(x, y)
   \]
3. Counting the number of operations performed.

It stops when the smallest element in the priority queue is **at least** `k`.

---

### **Example Dry Run**
#### **Input**
```java
nums = [1, 10, 12, 9, 2, 3]
k = 10
```

#### **Initial Setup**
- **Priority Queue (Min Heap) Initialization**  
  After inserting all elements into `pq`:
  ```
  pq = [1, 2, 3, 9, 10, 12]
  ```
  (Numbers are sorted in ascending order due to the min-heap property.)

- **Initialize** `count = 0`

---

### **Step-by-Step Execution**

#### **Iteration 1**
- **Smallest Element** `1` (less than `10` and `pq.size() >= 2`)  
- **Extract `1` and `2`**, compute new value:
  \[
  z = (1 \times 2) + 2 = 4
  \]
- **Insert `4` into the heap**  
  ```
  pq = [3, 4, 12, 9, 10]
  ```
- **Increment `count`** → `count = 1`

---

#### **Iteration 2**
- **Smallest Element** `3` (less than `10`)  
- **Extract `3` and `4`**, compute new value:
  \[
  z = (3 \times 2) + 4 = 10
  \]
- **Insert `10` into the heap**  
  ```
  pq = [9, 10, 12, 10]
  ```
- **Increment `count`** → `count = 2`

---

#### **Iteration 3**
- **Smallest Element** `9` (less than `10`)  
- **Extract `9` and `10`**, compute new value:
  \[
  z = (9 \times 2) + 10 = 28
  \]
- **Insert `28` into the heap**  
  ```
  pq = [10, 12, 28]
  ```
- **Increment `count`** → `count = 3`

---

#### **Termination Condition**
- Now, the smallest element in `pq` is `10`, which is **not less than** `k`.
- **Exit loop** and return `count = 3`.

---

### **Final Output**
```java
return 3;
```

---

### **Edge Cases**
| **Test Case**      | **Explanation** |
|--------------------|----------------|
| `nums = [10, 12, 15], k = 10` | No operation needed, return `0`. |
| `nums = [1, 1, 1, 1], k = 10` | Multiple operations required to reach `k`. |
| `nums = [9, 9, 9], k = 10` | One operation required. |

---

### **Time Complexity**
- **Heap Operations:** Each insertion/deletion takes **O(log n)**.
- **Loop Iterations:** Worst case **O(n)** (each operation reduces heap size).
- **Overall Complexity:** **O(n log n)**.

---
