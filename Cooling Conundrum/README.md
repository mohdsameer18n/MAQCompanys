# Cooling Conundrum

## Problem Statement

Chef wants to cool a dessert from an initial temperature **X** to a target temperature **Y** (`X > Y`).

If the current temperature is **K**, reducing it by **1 degree** takes:

\[
\lceil K/10 \rceil
\]

seconds.

After every 1-degree reduction, the cooling time is recalculated based on the new temperature.

Your task is to determine the total number of seconds required to cool the dessert from **X** to **Y**.

---

## Approach 1: Using `Math.ceil()`

### Algorithm
1. Read the number of test cases `T`.
2. For each test case:
   - Read `X` and `Y`.
   - Initialize `count = 0`.
   - While `X > Y`:
     - Compute `Math.ceil(X / 10.0)` and add it to `count`.
     - Decrease `X` by `1`.
3. Print the total time.

### Java Solution

```java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef
{
    public static void main (String[] args) throws java.lang.Exception
    {
        Scanner scan = new Scanner(System.in);
        int T = scan.nextInt();

        while (T-- > 0) {
            int X = scan.nextInt();
            int Y = scan.nextInt();
            int count = 0;

            while (X > Y) {
                count += (int) Math.ceil(X / 10.0);
                X--;
            }

            System.out.println(count);
        }
    }
}
```

### Complexity Analysis

- **Time Complexity:** `O(X - Y)`
- **Space Complexity:** `O(1)`

---

## Approach 2: Using Integer Arithmetic (Optimized)

### Key Observation

For positive integers,

```
ceil(X / 10) = (X + 9) / 10
```

This eliminates the need for floating-point calculations.

### Algorithm

1. Read the number of test cases `T`.
2. For each test case:
   - Read `X` and `Y`.
   - Initialize `count = 0`.
   - While `X > Y`:
     - Add `(X + 9) / 10` to `count`.
     - Decrease `X` by `1`.
3. Print the total time.

### Java Solution

```java
import java.util.*;

class Codechef
{
    public static void main(String[] args)
    {
        Scanner scan = new Scanner(System.in);
        int T = scan.nextInt();

        while (T-- > 0) {
            int X = scan.nextInt();
            int Y = scan.nextInt();
            int count = 0;

            while (X > Y) {
                count += (X + 9) / 10;
                X--;
            }

            System.out.println(count);
        }
    }
}
```

### Complexity Analysis

- **Time Complexity:** `O(X - Y)`
- **Space Complexity:** `O(1)`

---

## Example

### Input

```
4
38 37
61 58
15 5
100 1
```

### Output

```
4
19
15
549
```

---

## Comparison

| Feature | `Math.ceil()` | Integer Formula |
|---------|---------------|-----------------|
| Formula | `Math.ceil(X / 10.0)` | `(X + 9) / 10` |
| Floating Point | ✅ Yes | ❌ No |
| Performance | Good | Better |
| Time Complexity | `O(X - Y)` | `O(X - Y)` |
| Space Complexity | `O(1)` | `O(1)` |

---

## Recommendation

Both approaches are correct and pass all test cases.

- Use **`Math.ceil()`** if you want a straightforward mathematical implementation.
- Use the **integer formula `(X + 9) / 10`** for better performance, as it avoids floating-point operations and is the preferred approach in competitive programming.
