# Problem: 209 - Minimum Size Subarray Sum

## Problem Statement
Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target.<br>
If there is no such subarray, return 0 instead.
 
Example 1:

Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.

Example 2:

Input: target = 4, nums = [1,4,4]
Output: 1

Example 3:

Input: target = 11, nums = [1,1,1,1,1,1,1,1]
Output: 0
 
 ## Constraints:

1 <= target <= 109
1 <= nums.length <= 10^5
1 <= nums[i] <= 10^4

## Approach
Use a Sliding Window to find the smallest subarray whose sum is at least target.
-Expand the window by moving high and adding elements to sum.
-When sum >= target, update the minimum length and shrink the window from the left (low) to find a smaller valid subarray.
-Continue until the entire array is processed.
    
## Time Complexity
O(n)

## Space Complexity
O(1)

## Java Solution

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int low =0, high = 0, sum = 0;
        int res = Integer.MAX_VALUE;
        
        while(high < nums.length){
            sum+=nums[high];

            while(sum >= target){
                int len = high - low +1;
                if(len < res){
                    res = len;
                }
                sum -= nums[low];
                low++;
            }

            high++;
        }
        return res == Integer.MAX_VALUE? 0 : res;
    }
}
```
