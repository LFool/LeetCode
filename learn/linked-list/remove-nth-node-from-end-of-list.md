# Remove Nth Node From End of List

Given a linked list, remove the _n_-th node from the end of list and return its head.

**Example:**

> Given linked list: 1-&gt;2-&gt;3-&gt;4-&gt;5, and n = 2.
>
> After removing the second node from the end, the linked list becomes 1-&gt;2-&gt;3-&gt;5.

**Note:**

Given _n_ will always be valid.

**Follow up:**

Could you do this in one pass?

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode first = head;
        ListNode second = head;
        int count = 0;
        while (first != null) {
            if (count > n) second = second.next;
            first = first.next;
            count++;
        }
        if (count == n) return second.next;
        second.next = second.next.next == null ? null : second.next.next;
        return head;
    }
}
```

