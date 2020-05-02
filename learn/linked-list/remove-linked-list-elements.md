# Remove Linked List Elements

Remove all elements from a linked list of integers that have value **val**.

**Example:**

> **Input:** 1-&gt;2-&gt;6-&gt;3-&gt;4-&gt;5-&gt;6, val = 6 
>
> **Output:** 1-&gt;2-&gt;3-&gt;4-&gt;5

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        
        ListNode myHead = new ListNode(0);
        myHead.next = head;
        
        ListNode pre = myHead;
        
        while (pre.next != null) {
            if (pre.next.val == val) pre.next = pre.next.next;
            else pre = pre.next;
        }
        
        return myHead.next;
    }
}
```

