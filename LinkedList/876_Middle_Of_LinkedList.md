# Problem: 876 - Middle of the Linked List

## Problem Statement
Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

Example 1:

<img width="544" height="65" alt="image" src="https://github.com/user-attachments/assets/2cb875a6-de46-41f7-93aa-9c4989d4132e" />

Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.

Example 2:

<img width="544" height="65" alt="image" src="https://github.com/user-attachments/assets/c79fa5bb-bc49-4131-bcdb-37658a43ebe7" />

Input: head = [1,2,3,4,5,6]
Output: [4,5,6]
Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.
 
 ## Constraints:
 
The number of nodes in the list is in the range [1, 100].
1 <= Node.val <= 100

## Approach
-Traverse the linked list once to count total nodes
-Find the middle index using count / 2
-Traverse again from the head up to the middle node
-Return the middle node

## Time Complexity
O(n)

## Space Complexity
O(1)

## Java Solution

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        int count = 0;

        ListNode temp = head;

        while(temp!=null){
            count++;
            temp=temp.next;
        }
        
        temp = head;

        for(int i = 0; i < count/2; i++){
            temp = temp.next;
        }

        return temp;

    }
}
```
