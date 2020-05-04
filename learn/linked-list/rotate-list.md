# Rotate List

## Description

Given a linked list, rotate the list to the right by _k_ places, where _k_ is non-negative.

**Example 1:**

> **Input:** 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, k = 2 
>
> **Output:** 4-&gt;5-&gt;1-&gt;2-&gt;3-&gt;NULL 
>
> **Explanation:** 
>
> rotate 1 steps to the right: 5-&gt;1-&gt;2-&gt;3-&gt;4-&gt;NULL 
>
> rotate 2 steps to the right: 4-&gt;5-&gt;1-&gt;2-&gt;3-&gt;NULL

**Example 2:**

> **Input:** 0-&gt;1-&gt;2-&gt;NULL, k = 4 
>
> **Output:** 2-&gt;0-&gt;1-&gt;NULL 
>
> **Explanation:** 
>
> rotate 1 steps to the right: 2-&gt;0-&gt;1-&gt;NULL 
>
> rotate 2 steps to the right: 1-&gt;2-&gt;0-&gt;NULL 
>
> rotate 3 steps to the right: 0-&gt;1-&gt;2-&gt;NULL 
>
> rotate 4 steps to the right: 2-&gt;0-&gt;1-&gt;NULL

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
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null) return  null;
        
        ListNode first = head;
        ListNode second = head;
        int size = 0;
        while(first != null) {
            size++;
            first = first.next;
        }
        
        k %= size;
        
        first = head;
        int count = 1;
        while (first != null && first.next != null) {
            if (count > k) second = second.next;
            first = first.next;
            count++;
        }
        
        first.next = head;
        
        ListNode result = second.next;
        
        second.next = null;
        
        return result;

    }
}
```

