# Odd Even Linked List

## Description

Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.

You should try to do it in place. The program should run in O\(1\) space complexity and O\(nodes\) time complexity.

**Example 1:**

> **Input:** 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL 
>
> **Output:** 1-&gt;3-&gt;5-&gt;2-&gt;4-&gt;NULL

**Example 2:**

> **Input:** 2-&gt;1-&gt;3-&gt;5-&gt;6-&gt;4-&gt;7-&gt;NULL 
>
> **Output:** 2-&gt;3-&gt;6-&gt;7-&gt;1-&gt;5-&gt;4-&gt;NULL

**Note:**

* The relative order inside both the even and odd groups should remain as it was in the input.
* The first node is considered odd, the second node even and so on ...

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
    public ListNode oddEvenList(ListNode head) {
        
        ListNode myHead = new ListNode(0);
        myHead.next =head;
        ListNode tail = myHead;
        int size = 0;
        
        while (tail.next != null) {
            tail = tail.next;
            size++;
        }
        
        ListNode pre = myHead;
        for (int i = 1; i <= size; i++) {
            if (i % 2 == 0) {
                tail.next = pre.next;
                tail = tail.next;
                pre.next = pre.next.next;
                i++;
            }
            pre = pre.next;
        }
        tail.next = null;
        
        return myHead.next;
        
        
    }
}
```

