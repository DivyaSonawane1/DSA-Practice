# Problem: 977 - Squares of sorted Array

## Problem Statement
Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

Example 1:

Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
Example 2:

Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
 
 ## Constraints:

1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums is sorted in non-decreasing order.

## Follow up:
Squaring each element and sorting the new array is very trivial, could you find an O(n) solution using a different approach?

## Approach
Two-Pointer Approach 
Take two pointers:
left = 0
right = n-1
Compare:
nums[left]^2
nums[right]^2
Put the larger square at the end of the answer array.
Move the corresponding pointer.
Continue until left > right.

## Time Complexity
O(n)

## Space Complexity
O(n)

## Java Solution

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int n = nums.length;
        int[] res = new int[n];

        int left = 0, right = n - 1;
        int index = n - 1;

        while (left <= right) {
            int leftSq = nums[left] * nums[left];
            int rightSq = nums[right] * nums[right];

            if (leftSq > rightSq) {
                res[index] = leftSq;
                index--;
                left++;
            } else {
                res[index] = rightSq;
                right--;  
                index--;
            }
        }

        return res;
    }
}
```
