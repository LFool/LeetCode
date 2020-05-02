# Linked List Cycle II

Given a linked list, return the node where the cycle begins. If there is no cycle, return `null`.

To represent a cycle in the given linked list, we use an integer `pos` which represents the position \(0-indexed\) in the linked list where tail connects to. If `pos` is `-1`, then there is no cycle in the linked list.

**Note:** Do not modify the linked list.

**Example 1:**

> **Input:** head = \[3,2,0,-4\], pos = 1 
>
> **Output:** tail connects to node index 1 
>
> **Explanation**: There is a cycle in the linked list, where tail connects to the second node.

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

**Example 2:**

> **Input:** head = \[1,2\], pos = 0 
>
> **Output:** tail connects to node index 0 
>
> **Explanation:** There is a cycle in the linked list, where tail connects to the first node.

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

**Example 3:**

> **Input:** head = \[1\], pos = -1 
>
> **Output:** no cycle 
>
> **Explanation:** There is no cycle in the linked list.

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)

**Follow-up**:  
Can you solve it without using extra space?



![](../../.gitbook/assets/image%20%289%29.png)

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        boolean isCycle = false;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                isCycle = true;
                break;
            }
        }
        if (!isCycle) return null;
        // 新定义一个节点result从头开始和slow同步移动
        // 当result和slow相遇时，slow移动了x3的距离，result移动了x1的距离
        // result正好到达最初相遇的点
        ListNode result = head;
        while (result != slow) {
            result =result.next;
            slow = slow.next;
        }
        return result;
    }
}
```

