# Contains Duplicate (LeetCode #217)

## Problem Link

https://leetcode.com/problems/contains-duplicate/

---

## Problem Summary

Given an integer array, determine if any value appears at least twice in the array. Return true if any duplicate exists, otherwise return false.

---

## Intuition

My first approach was to sort the array and compare elements using nested loops. This was inefficient and resulted in poor performance.

To optimize, I realized that duplicates can be detected using a HashSet. Since a set only stores unique elements, comparing sizes or detecting insertion failure can help identify duplicates efficiently.

---

## Approach

Two optimized approaches using a HashSet:

1. Convert the array into a set and compare sizes:

   * If the size of the set is equal to the array length → no duplicates
   * Otherwise → duplicates exist

2. Traverse the array and try adding elements to a set:

   * If adding an element fails, it means it already exists → duplicate found

The second approach is more efficient as it exits early when a duplicate is found.

---

## Algorithm Steps

1. Create an empty HashSet
2. Traverse through each element in the array
3. Try to add the element to the set
4. If addition fails, return true
5. If loop completes, return false

---

## Code (Java)

```java
import java.util.HashSet;

class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();

        for (int num : nums) {
            if (!set.add(num)) {
                return true;
            }
        }

        return false;
    }
}
```

---

## Complexity Analysis

* Time Complexity: O(n)
* Space Complexity: O(n)

---

## Example Walkthrough

Input:

```
nums = [1, 2, 3, 1]
```

Output:

```
true
```

Explanation:

* Add 1 → set = {1}
* Add 2 → set = {1, 2}
* Add 3 → set = {1, 2, 3}
* Add 1 again → already exists → return true

---

## Key Takeaways

* HashSet is useful for detecting duplicates efficiently
* Sorting + nested loops is inefficient compared to hashing
* Early exit improves performance

---

## Tags

Array, HashSet

---

## Notes

An alternative approach is to convert the array into a set and compare sizes, but it does not allow early termination.
