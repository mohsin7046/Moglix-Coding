# Longest Valid Parentheses

## Problem

Given a string containing only `'('` and `')'`, return the length of the **longest valid (well-formed) parentheses substring**.

### Examples

```text
Input: "(()"
Output: 2

Input: ")()())"
Output: 4

Input: ""
Output: 0
```

**Constraints**

* `0 <= s.length <= 3 * 10^4`
* `s[i]` is either `'('` or `')'`

---

## Approaches

### 1. Stack Approach

**Idea**

* Store indices of parentheses in a stack.
* Initialize the stack with `-1` as the base index.
* Push the index of every `'('`.
* For every `')'`, pop the stack.

  * If the stack becomes empty, push the current index as the new base.
  * Otherwise, calculate the current valid substring length using `currentIndex - stack.peek()`.

**Complexity**

* **Time:** `O(n)`
* **Space:** `O(n)`

---

### 2. Two-Pass Counter Approach (Optimal Space)

**Idea**

Perform two scans using only two counters (`left` and `right`):

* **Left → Right**

  * Increment `left` for `'('` and `right` for `')'`.
  * When `left == right`, update the maximum length.
  * If `right > left`, reset both counters.

* **Right → Left**

  * Repeat the same process in reverse.
  * Reset when `left > right`.

This second pass handles cases with extra opening parentheses that the first pass cannot detect.

**Complexity**

* **Time:** `O(n)`
* **Space:** `O(1)`

---

## Repository Contents

* `LongestValidParanthesesStack.java` – Stack-based solution
* `LongestValidParanthesesTwoPointer.java` – Two-pass counter solution

---

## Summary

| Approach         | Time   | Space  |
| ---------------- | ------ | ------ |
| Stack            | `O(n)` | `O(n)` |
| Two-Pass Counter | `O(n)` | `O(1)` |

Both solutions pass all standard and edge test cases.
