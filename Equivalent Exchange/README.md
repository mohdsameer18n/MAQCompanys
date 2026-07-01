# Equivalent Exchange

## Problem Statement

A shop contains **K** stones in total, consisting of **red** and **blue** stones.

Initially, the shopkeeper chooses an integer **X** (`0 ≤ X ≤ K`) and starts with:

- **X** red stones
- **K − X** blue stones

There are **N** customers, each requesting a trade:

- If `Ai > 0`:
  - Customer gives `Ai` red stones.
  - Customer takes `Ai` blue stones.
- If `Ai < 0`:
  - Customer gives `-Ai` blue stones.
  - Customer takes `-Ai` red stones.

Determine whether there exists an initial value of **X** such that the shop never has a negative number of red or blue stones throughout all trades.

---

# Approach

Instead of trying every possible value of **X**, we determine the valid range of **X** while processing the trades.

Let:

- `prefix` = cumulative change in the number of red stones.

Initially:

- Red = `X`
- Blue = `K - X`

After processing some trades:

- Red = `X + prefix`
- Blue = `K - X - prefix`

For every transaction:

- Red stones must remain non-negative.

```
X + prefix ≥ 0
```

which gives

```
X ≥ -prefix
```

- Blue stones must remain non-negative.

```
K - X - prefix ≥ 0
```

which gives

```
X ≤ K - prefix
```

Thus, after every trade we update:

- Lower bound of `X`
- Upper bound of `X`

If, after processing all trades, the valid range is non-empty, the answer is **Yes**; otherwise **No**.

---

# Algorithm

1. Read `T`.
2. For each test case:
   - Read `N` and `K`.
   - Initialize:
     - `prefix = 0`
     - `low = 0`
     - `high = K`
   - For each transaction:
     - Update `prefix += Ai`.
     - Update:
       - `low = max(low, -prefix)`
       - `high = min(high, K - prefix)`
3. If `low <= high`, print `"Yes"`; otherwise print `"No"`.

---

# Correctness

Let `prefix` denote the cumulative change in red stones after processing some trades.

At any point:

- Red stones = `X + prefix`
- Blue stones = `K - X - prefix`

To ensure both counts remain non-negative:

- `X + prefix ≥ 0`
- `K - X - prefix ≥ 0`

These inequalities define the valid interval for the initial number of red stones.

The algorithm continuously intersects these intervals after every trade.

- If the final interval is non-empty, there exists a valid starting value of `X`, so every trade can be completed.
- Otherwise, no such initial configuration exists.

Hence, the algorithm is correct.

---

# Complexity Analysis

- **Time Complexity:** `O(N)` per test case
- **Space Complexity:** `O(1)`

---

# Java Solution

```java
import java.util.*;

class Codechef {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int T = sc.nextInt();

        while (T-- > 0) {
            int N = sc.nextInt();
            int K = sc.nextInt();

            int prefix = 0;
            int low = 0;
            int high = K;

            for (int i = 0; i < N; i++) {
                int a = sc.nextInt();
                prefix += a;

                low = Math.max(low, -prefix);
                high = Math.min(high, K - prefix);
            }

            System.out.println(low <= high ? "Yes" : "No");
        }

        sc.close();
    }
}
```

---

# Example

### Input

```
4
3 10
5 2 -9
2 3
2 2
4 12
-4 -7 8 -10
4 8
8 -8 8 -8
```

### Output

```
Yes
No
No
Yes
```

---

# Key Insight

Instead of checking every possible initial value of **X**, maintain the **valid interval** of `X` throughout the trades. If the interval is still valid after all transactions, the answer is **Yes**; otherwise **No**.
