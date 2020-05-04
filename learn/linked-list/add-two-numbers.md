# Add Two Numbers

## Description

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**

> **Input:** \(2 -&gt; 4 -&gt; 3\) + \(5 -&gt; 6 -&gt; 4\) 
>
> **Output:** 7 -&gt; 0 -&gt; 8 
>
> **Explanatio**n: 342 + 465 = 807.

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode preHead = new ListNode(0);
        ListNode node = preHead;
        int sum = 0;
        while (l1 != null || l2 != null) {
            sum /= 10;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            node.next = new ListNode(sum % 10);
            node = node.next;
        }
        if (sum / 10 != 0) node.next = new ListNode(sum / 10);
        return preHead.next;
    }

}
```

