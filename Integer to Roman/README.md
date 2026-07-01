# 12. Integer to Roman

## Problem Statement

Given an integer `num`, convert it to its corresponding Roman numeral.

Roman numerals are represented by the following seven symbols:

| Symbol | Value |
| :----: | ----: |
|    I   |     1 |
|    V   |     5 |
|    X   |    10 |
|    L   |    50 |
|    C   |   100 |
|    D   |   500 |
|    M   |  1000 |

Roman numerals also include the following subtraction rules:

* IV = 4
* IX = 9
* XL = 40
* XC = 90
* CD = 400
* CM = 900

---

## Approach

This solution uses a **Greedy Algorithm**.

* Store all Roman numeral values in descending order, including the six subtraction cases.
* Traverse the arrays from largest to smallest value.
* While the current value is less than or equal to the remaining number:

  * Append the corresponding Roman symbol.
  * Subtract that value from the number.
* Continue until the number becomes `0`.

Since the number of Roman symbols is fixed, the algorithm runs in constant time.

---

## Algorithm

1. Create two arrays:

   * One containing Roman numeral values.
   * One containing the corresponding Roman symbols.
2. Initialize an empty `StringBuilder`.
3. Iterate through each value from largest to smallest.
4. While `num >= value`:

   * Append the corresponding symbol.
   * Subtract the value from `num`.
5. Return the final Roman numeral string.

---

## Complexity Analysis

* **Time Complexity:** `O(1)`
* **Space Complexity:** `O(1)`

---

## Example

### Input

```text
num = 1994
```

### Output

```text
MCMXCIV
```

### Explanation

```text
1994
= 1000 + 900 + 90 + 4
= M + CM + XC + IV
= MCMXCIV
```

---

## Java Solution

```java
class Solution {
    public String intToRoman(int num) {

        int[] values = {
            1000, 900, 500, 400,
            100, 90, 50, 40,
            10, 9, 5, 4, 1
        };

        String[] symbols = {
            "M", "CM", "D", "CD",
            "C", "XC", "L", "XL",
            "X", "IX", "V", "IV", "I"
        };

        StringBuilder ans = new StringBuilder();

        for (int i = 0; i < values.length; i++) {
            while (num >= values[i]) {
                ans.append(symbols[i]);
                num -= values[i];
            }
        }

        return ans.toString();
    }
}
```

---

## Key Concepts

* Greedy Algorithm
* Array Traversal
* StringBuilder
* Simulation
* Roman Numeral Conversion
