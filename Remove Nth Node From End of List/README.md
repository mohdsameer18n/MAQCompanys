# 19. Remove Nth Node From End of List

## Problem Statement

Given the `head` of a linked list, remove the **n<sup>th</sup> node from the end** of the list and return its head.

---

## Approach

This problem can be solved efficiently using the **Two Pointers (Fast & Slow)** technique.

1. Create a **dummy node** pointing to the head. This helps handle edge cases such as deleting the first node.
2. Initialize two pointers, `fast` and `slow`, at the dummy node.
3. Move the `fast` pointer `n + 1` steps ahead.
4. Move both pointers one step at a time until `fast` reaches the end of the list.
5. At this point, `slow` is just before the node to be removed.
6. Remove the target node by updating `slow.next`.
7. Return `dummy.next`.

Using a dummy node simplifies handling all edge cases without additional conditions.

---

## Algorithm

1. Create a dummy node pointing to `head`.
2. Initialize `fast` and `slow` to the dummy node.
3. Move `fast` forward by `n + 1` nodes.
4. Move both pointers together until `fast` becomes `null`.
5. Remove the target node using:

   ```java
   slow.next = slow.next.next;
   ```
6. Return `dummy.next`.

---

## Complexity Analysis

* **Time Complexity:** `O(N)`

  * Traverse the linked list only once.

* **Space Complexity:** `O(1)`

  * Only two pointers are used.

---

## Example

### Input

```text
head = [1,2,3,4,5], n = 2
```

### Output

```text
[1,2,3,5]
```

### Explanation

```text
Original List:
1 → 2 → 3 → 4 → 5

2nd node from the end = 4

After removing 4:
1 → 2 → 3 → 5
```

---

## Java Solution

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {

        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode fast = dummy;
        ListNode slow = dummy;

        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        slow.next = slow.next.next;

        return dummy.next;
    }
}
```

---

## Key Concepts

* Linked List
* Two Pointers
* Fast & Slow Pointer
* Dummy Node
* One Pass Algorithm
* Pointer Manipulation
