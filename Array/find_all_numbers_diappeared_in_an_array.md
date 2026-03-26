# Find All Numbers Disappeared in an Array (LeetCode #448)

## Problem Link

https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/

---

## Problem Summary

Given an array of integers where 1 ≤ nums[i] ≤ n (n = size of array), some elements appear twice and others appear once. Find all the numbers in the range [1, n] that do not appear in the array.

---

## Intuition

The idea was to store all elements of the array in a HashSet for fast lookup. Then, iterate from 1 to n and check which numbers are not present in the set. Those missing numbers are added to the result list.

---

## Approach

* Use a HashSet to store all elements from the array
* Traverse numbers from 1 to n
* For each number, check if it exists in the set
* If not, add it to the result list

---

## Algorithm Steps

1. Create a HashSet and add all elements of the array
2. Create an empty list to store missing numbers
3. Loop from 1 to n (array length)
4. If a number is not in the set, add it to the list
5. Return the list

---

## Code (Java)

```java
import java.util.*;

class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        Set<Integer> a = new HashSet<>();

        for (int n : nums) {
            a.add(n);
        }

        List<Integer> l1 = new ArrayList<>();

        for (int i = 1; i <= nums.length; i++) {
            if (!a.contains(i)) {
                l1.add(i);
            }
        }

        return l1;
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
nums = [4,3,2,7,8,2,3,1]
```

Output:

```
[5,6]
```

Explanation:

* Numbers from 1 to 8 should be present
* Missing numbers are 5 and 6

---

## Notes

This approach is simple and efficient but uses extra space.
An optimized solution exists that modifies the array in-place to achieve O(1) extra space.
