# Two Sum (LeetCode #1)

## Problem Link

https://leetcode.com/problems/two-sum/

---

## Problem Summary

Given an array of integers and a target value, return the indices of the two numbers such that they add up to the target.

---

## Intuition

The brute-force approach is to check all pairs using nested loops, but that results in O(n²) time complexity.

To optimize, I used a HashMap to store elements as I iterate through the array. For each element, I calculate its complement (target - current value) and check if it already exists in the map. If it does, I have found the required pair.

---

## Approach

* Create a HashMap to store elements and their indices
* Traverse the array once
* For each element:

  * Calculate complement = target - current value
  * Check if complement exists in the map
  * If yes, return indices
  * Otherwise, store the current element in the map

---

## Algorithm Steps

1. Initialize an empty HashMap
2. Loop through the array
3. For each index `i`, compute `complement = target - nums[i]`
4. If complement exists in the map, return `[map.get(complement), i]`
5. Otherwise, store `nums[i]` with index `i` in the map
6. Return an empty array (to satisfy Java syntax)

---

## Code (Java)

```java
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> hm = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int comp = target - nums[i];

            if (hm.containsKey(comp)) {
                return new int[]{hm.get(comp), i};
            } else {
                hm.put(nums[i], i);
            }
        }

        return new int[]{}; // fallback return
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
nums = [2, 7, 11, 15], target = 9
```

Output:

```
[0, 1]
```

Explanation:

* Start with empty map
* i = 0 → num = 2 → complement = 7 → not in map → store {2:0}
* i = 1 → num = 7 → complement = 2 → found in map → return [0,1]

---

## Notes

This approach improves performance from O(n²) to O(n).
The fallback return statement is for satisfying the compiler :/
