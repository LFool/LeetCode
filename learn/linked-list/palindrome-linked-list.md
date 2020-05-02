# Palindrome Linked List

Given a singly linked list, determine if it is a palindrome.

**Example 1:**

> **Input:** 1-&gt;2 
>
> **Output:** false

**Example 2:**

> **Input:** 1-&gt;2-&gt;2-&gt;1 
>
> **Output:** true

**Follow up:**  
Could you do it in O\(n\) time and O\(1\) space?

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
    public boolean isPalindrome(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while (fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;
        }
        if (fast != null) slow = slow.next;
        slow = reverse(slow);
        ListNode tHead = head;
        while (slow != null) {
            if (slow.val != tHead.val) return false;
            slow = slow.next;
            tHead = tHead.next;
        }
        return true;
    }
    
    public ListNode reverse(ListNode head) {
        ListNode newHead = null;
        while (head != null) {
            ListNode next = head.next;
            head.next = newHead;
            newHead = head;
            head = next;
        }
        return newHead;
    }
}
```

