# Missing Number (LeetCode #268)

## Problem Link

https://leetcode.com/problems/missing-number/

---

## Problem Summary

Given an array containing n distinct numbers in the range [0, n], return the only number that is missing from the array.

---

## Intuition

My initial idea was to generate numbers from 0 to n and check which one is missing in the given array, but that approach would be inefficient.

Then I realized that if I calculate the sum of numbers from 0 to n and subtract the sum of the given array, the result will be the missing number.

---

## Approach

* Calculate the sum of numbers from 0 to n using a loop
* Calculate the sum of elements in the given array
* Subtract the array sum from the expected sum to get the missing number

---

## Algorithm Steps

1. Initialize two variables: `asum` (expected sum) and `rsum` (array sum)
2. Loop from 0 to n and calculate `asum`
3. Loop through the array and calculate `rsum`
4. Return `asum - rsum`

---

## Code (Java)

```java
class Solution {
    public int missingNumber(int[] nums) {
        int asum = 0;
        int rsum = 0;

        for (int i = 0; i <= nums.length; i++) {
            asum += i;
        }

        for (int num : nums) {
            rsum += num;
        }

        int mn = asum - rsum;
        return mn;
    }
}
```

---

## Complexity Analysis

* Time Complexity: O(n)
* Space Complexity: O(1)

---

## Example Walkthrough

Input:

```
nums = [3, 0, 1]
```

Output:

```
2
```

Explanation:

* asum = 0 + 1 + 2 + 3 = 6
* rsum = 3 + 0 + 1 = 4
* Missing number = 6 - 4 = 2

---

## Notes

This approach uses loops to calculate the expected sum instead of the formula.
It is simple and avoids any risk of integer overflow from multiplication.
