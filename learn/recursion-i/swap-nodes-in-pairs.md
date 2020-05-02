# Swap Nodes in Pairs

Given a linked list, swap every two adjacent nodes and return its head.

You may **not** modify the values in the list's nodes, only nodes itself may be changed.

**Example:**

> Given 1-&gt;2-&gt;3-&gt;4, you should return the list as 2-&gt;1-&gt;4-&gt;3.

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
    public ListNode swapPairs(ListNode head) {
        if (head ==  null) return null;
        if (head.next == null) return head;
        
        ListNode newHead = swapPairs(head.next.next);
        
        ListNode temp = head.next;
        head.next.next = head;
        head.next = newHead;
        
        return temp;
    }
}
```

