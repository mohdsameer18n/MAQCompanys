# Move All Occurrences of an Element to the Front

## Problem Statement

Given an array of integers and a target element `k`, move all occurrences of `k` to the beginning of the array using **O(1)** extra space.

> **Note:** The relative order of the remaining elements is **not preserved**.

---

## Example

### Input
```
6
2 1 3 2 4 2
2
```

### Output
```
2 2 2 1 4 3
```

---

## Approach

- Use two pointers:
  - `l` points to the next position where `k` should be placed.
  - `m` traverses the array.
- Whenever `nums[m] == k`, swap `nums[l]` and `nums[m]`.
- Increment both pointers.
- This performs the operation in-place without using extra memory.

---

## Java Code

```java
import java.util.*;

public class MoveElementToFront {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        int n = scan.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = scan.nextInt();
        }

        int k = scan.nextInt();

        int l = 0;

        for (int m = 0; m < n; m++) {
            if (nums[m] == k) {
                int temp = nums[l];
                nums[l] = nums[m];
                nums[m] = temp;
                l++;
            }
        }

        for (int num : nums) {
            System.out.print(num + " ");
        }
    }
}
```

---

## Time Complexity

- **O(n)**

## Space Complexity

- **O(1)**

---

## Concepts Used

- Arrays
- Two Pointers
- In-place Swapping

---

## Tags

`Array` `Two Pointers` `In-place Algorithm`
