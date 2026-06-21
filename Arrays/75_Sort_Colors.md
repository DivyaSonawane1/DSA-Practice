# Problem: 75 - Sort Colors

## Problem Statement
Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.
 
Example 1:

Input: nums = [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]

Example 2:

Input: nums = [2,0,1]
Output: [0,1,2]
 
 ## Constraints:

n == nums.length
1 <= n <= 300
nums[i] is either 0, 1, or 2.

## Approach
-We maintain three pointers:
  low → position where next 0 should be placed
  mid → current element being processed
  high → position where next 2 should be placed
-Cases
  1.If nums[mid] == 0
    -Swap nums[low] and nums[mid]
    -Increment low and mid
  2.If nums[mid] == 1
    -It is already in the correct region
    -Increment mid
  3.If nums[mid] == 2
    -Swap nums[mid] and nums[high]
    -Decrement high
    -Do not increment mid because the swapped element from high still needs to be checked
## Time Complexity
O(n)

## Space Complexity
O(1)

## Java Solution

```java
class Solution {
    public void sortColors(int[] nums) {
        int low = 0 ; 
        int high = nums.length-1;
        int mid = 0;

        while(mid <= high){
            if(nums[mid] == 0){
                int temp = nums[low];
                nums[low] = nums[mid];
                nums[mid] = temp;

                low++;
                mid++;
            }else if(nums[mid] == 1){
                
                mid++;
            }else{
                int temp = nums[high];
                nums[high] = nums[mid];
                nums[mid] = temp;
                high--;
            }
        }
    }
}
```
