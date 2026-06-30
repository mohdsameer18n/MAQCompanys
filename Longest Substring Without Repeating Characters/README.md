# 3. Longest Substring Without Repeating Characters

## Problem Statement

Given a string `s`, find the length of the **longest substring** without repeating characters.

A **substring** is a contiguous sequence of characters within a string.

---

## Examples

### Example 1

**Input**

```text
s = "abcabcbb"
```

**Output**

```text
3
```

**Explanation**

The longest substring without repeating characters is `"abc"`.

---

### Example 2

**Input**

```text
s = "bbbbb"
```

**Output**

```text
1
```

**Explanation**

The longest substring is `"b"`.

---

### Example 3

**Input**

```text
s = "pwwkew"
```

**Output**

```text
3
```

**Explanation**

The longest substring is `"wke"`.

---

## Approach

This problem is solved using the **Sliding Window** technique.

* Use two pointers:

  * `left` – start of the current window.
  * `right` – end of the current window.
* Maintain a `HashSet` to store unique characters in the current window.
* If the current character already exists in the set, remove characters from the left until the duplicate is removed.
* Add the current character to the set.
* Update the maximum window length.

This ensures each character is processed at most twice, resulting in an efficient solution.

---

## Algorithm

1. Initialize a `HashSet`.
2. Set `left = 0` and `maxLength = 0`.
3. Traverse the string using `right`.
4. While the current character is already present in the set:

   * Remove the character at `left`.
   * Increment `left`.
5. Add the current character to the set.
6. Update `maxLength`.
7. Return `maxLength`.

---

## Java Solution

```java
import java.util.HashSet;

class Solution {
    public int lengthOfLongestSubstring(String s) {

        HashSet<Character> set = new HashSet<>();

        int left = 0;
        int maxLength = 0;

        for (int right = 0; right < s.length(); right++) {

            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }

            set.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }
}
```

---

## Dry Run

**Input**

```text
s = "abba"
```

| Left | Right | Window          | Max Length |
| ---- | ----: | --------------- | ---------: |
| 0    |     0 | a               |          1 |
| 0    |     1 | ab              |          2 |
| 0    |     2 | abb (duplicate) |          2 |
| 2    |     2 | b               |          2 |
| 2    |     3 | ba              |          2 |

**Output**

```text
2
```

---

## Complexity Analysis

* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(min(n, charset))`

---

## Concepts Used

* Sliding Window
* Two Pointers
* HashSet
* String Processing

---

## Tags

`String` `HashSet` `Sliding Window` `Two Pointers` `LeetCode` `Medium`
