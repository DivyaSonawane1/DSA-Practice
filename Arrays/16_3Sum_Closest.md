# Problem:16 - 3Sum Closest

## Problem Statement
Given an integer array nums of length n and an integer target, find three integers at distinct indices in nums such that the sum is closest to target.

Return the sum of the three integers.

You may assume that each input would have exactly one solution.

Example 1:

Input: nums = [-1,2,1,-4], target = 1
Output: 2
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

Example 2:

Input: nums = [0,0,0], target = 1
Output: 0
Explanation: The sum that is closest to the target is 0. (0 + 0 + 0 = 0).
 
 ## Constraints:

3 <= nums.length <= 500
-1000 <= nums[i] <= 1000
-10^4 <= target <= 10^4

## Approach
- Sort the array.
- Initialize closestSum with the sum of the first three elements.
- Fix one element nums[i].
- Use two pointers:
    left = i + 1
    right = n - 1
- Calculate currSum = nums[i] + nums[left] + nums[right].
- If |target - currSum| < |target - closestSum|, update closestSum.
- Move pointers:
    If currSum < target → left++
    If currSum > target → right--
    If currSum == target → return target.
- Return closestSum after checking all possible triplets.


## Time Complexity
O(n²)

## Space Complexity
O(1)

## Java Solution

```java
class Solution {
    public int threeSumClosest(int[] nums, int target) {
           int res_sum = 0;
        Arrays.sort(nums);
        int max_diff = Integer.MAX_VALUE;

        for(int i = 0; i < nums.length-2; i++){
             int left = i+1, right = nums.length-1;

        while(left<right){
             int sum = nums[i]+nums[left]+nums[right];

             int diff = Math.abs(sum-target);
             if(max_diff>diff){
                max_diff = diff;
                res_sum = sum;
             }
            if(sum == target){
                res_sum = sum;
                left++;
                right--;
                
            }else if(sum<target) left++;
            else right--;
        }
        }
        return res_sum;
    }
}
```
