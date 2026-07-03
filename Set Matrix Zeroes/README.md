# LeetCode 73 - Set Matrix Zeroes

## Problem Statement
Given an `m x n` integer matrix `matrix`, if an element is `0`, set its entire row and column to `0`. The operation must be performed **in-place**.

### Example

**Input:**
```text
matrix = [
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
```

**Output:**
```text
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]
```

---

## Approach (Using Extra Space)

### Idea
1. Traverse the matrix to identify all rows and columns containing `0`.
2. Store this information using two boolean arrays:
   - `row[]` → Marks rows that need to be zeroed.
   - `col[]` → Marks columns that need to be zeroed.
3. Traverse the matrix again.
4. If a cell belongs to a marked row or column, set it to `0`.

This approach ensures that newly assigned zeros do not affect the original traversal.

---

## Algorithm

1. Create two boolean arrays:
   - `row[n]`
   - `col[m]`
2. Traverse the matrix.
3. Whenever `matrix[i][j] == 0`:
   - Mark `row[i] = true`
   - Mark `col[j] = true`
4. Traverse the matrix again.
5. If `row[i]` or `col[j]` is `true`, set `matrix[i][j] = 0`.

---

## Java Solution

```java
class Solution {
    public void setZeroes(int[][] matrix) {

        int n = matrix.length;
        int m = matrix[0].length;

        boolean[] row = new boolean[n];
        boolean[] col = new boolean[m];

        // Mark rows and columns containing zero
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (matrix[i][j] == 0) {
                    row[i] = true;
                    col[j] = true;
                }
            }
        }

        // Set corresponding rows and columns to zero
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (row[i] || col[j]) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
```

---

## Dry Run

### Input

```text
1 1 1
1 0 1
1 1 1
```

### Step 1: Mark Rows and Columns

Zero found at `(1,1)`.

```text
row = [false, true, false]
col = [false, true, false]
```

### Step 2: Update Matrix

Cells in row `1` or column `1` become `0`.

```text
1 0 1
0 0 0
1 0 1
```

---

## Complexity Analysis

- **Time Complexity:** `O(m × n)`
- **Space Complexity:** `O(m + n)`

---

## Key Takeaways

- Two-pass traversal prevents newly assigned zeros from affecting the result.
- Boolean arrays efficiently store rows and columns that need modification.
- Easy to understand and implement.
- An optimized solution exists with **O(1)** extra space by using the first row and first column as markers.

---

## Topics

- Arrays
- Matrix
- Simulation
- In-Place Algorithm
