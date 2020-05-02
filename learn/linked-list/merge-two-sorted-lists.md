# Merge Two Sorted Lists

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

> **Input:** 1-&gt;2-&gt;4, 1-&gt;3-&gt;4 
>
> **Output:** 1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4

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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode preHead = new ListNode(0);
        preHead.next = l1;
        ListNode myHead = preHead;
        ListNode next = null;
        while (myHead.next != null && l2 != null) {
            if (myHead.next.val <= l2.val) {
                myHead = myHead.next;
                continue;
            }
            next = l2.next;
            l2.next = myHead.next;
            myHead.next = l2;
            l2 = next;
        }
        if (l2 != null) myHead.next = l2;
        return preHead.next;
    }
}
```



