# Reverse Linked List

## Description

Reverse a singly linked list.

**Example:**

> **Input:** 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL 
>
> **Output:** 5-&gt;4-&gt;3-&gt;2-&gt;1-&gt;NULL

**Follow up:**

A linked list can be reversed either iteratively or recursively. Could you implement both?

## **Code**

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
    public ListNode reverseList(ListNode head) {
        return reverseListByRecur(head, null);
    }
    public ListNode reverseListByIterate(ListNode head) {
        ListNode newHead = null;
        while (head != null) {
            ListNode next = head.next;
            head.next = newHead;
            newHead = head;
            head = next;
        }
        return newHead;
    }
    public ListNode reverseListByRecur(ListNode head, ListNode newHead) {
        if (head == null) {
            return newHead;
        }
        ListNode next = head.next;
        head.next = newHead;
        return reverseListByRecur(next, head);
    }
}
```

