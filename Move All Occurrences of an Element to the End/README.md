# Move All Occurrences of an Element to the End

## Problem Statement

Given an array of integers and a target element `k`, move all occurrences of `k` to the end of the array using **O(1)** extra space.

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
4 1 3 2 2 2
```

---

## Approach

- Use a pointer `r` to track the last available position.
- Traverse the array from right to left.
- Skip elements that are already equal to `k`.
- Whenever `k` is found, swap it with the element at pointer `r`.
- Decrement `r` after each swap.

---

## Java Code

```java
import java.util.*;

public class MoveElementToLast {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        int n = scan.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = scan.nextInt();
        }

        int k = scan.nextInt();

        int r = n - 1;

        for (int i = n - 1; i >= 0; i--) {

            while (r >= 0 && nums[r] == k) {
                r--;
            }

            if (i < r && nums[i] == k) {
                int temp = nums[i];
                nums[i] = nums[r];
                nums[r] = temp;
                r--;
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
