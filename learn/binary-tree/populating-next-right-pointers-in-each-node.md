# Populating Next Right Pointers in Each Node



You are given a **perfect binary tree** where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:

```java
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;
};
```

Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to `NULL`.

Initially, all next pointers are set to `NULL`.

**Follow up:**

* You may only use constant extra space.
* Recursive approach is fine, you may assume implicit stack space does not count as extra space for this problem.

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/02/14/116_sample.png)

> **Input:** root = \[1,2,3,4,5,6,7\] 
>
> **Output:** \[1,\#,2,3,\#,4,5,6,7,\#\] 
>
> **Explanation:** Given the above perfect binary tree \(Figure A\), your function should populate each next pointer to point to its next right node, just like in Figure B. The serialized output is in level order as connected by the next pointers, with '\#' signifying the end of each level.

**Constraints:**

* The number of nodes in the given tree is less than `4096`.
* `-1000 <= node.val <= 1000`

{% tabs %}
{% tab title="Non-recursive - 01" %}
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}
    
    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
};
*/

class Solution {
    public Node connect(Node root) {
        
        if (root == null) return null;
        
        Queue<Node> queue = new LinkedList<>();
        queue.add(root);
        
        while (!queue.isEmpty()) {
            
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                Node node = queue.poll();
                if (i < size - 1) {
                    node.next = queue.peek();
                }
                if (node.left != null) queue.add(node.left);
                if (node.right != null) queue.add(node.right);
            }
        }
        
        return root;
    }
}
```
{% endtab %}

{% tab title="Non-recursive - 02" %}
```java
public Node connect(Node root) {
    Node copyRoot = root;
    while (copyRoot != null) {
        Node cur = copyRoot;
        while (cur != null) {
            if (cur.left != null) cur.left.next = cur.right;
            if (cur.right != null && cur.next != null) cur.right.next = cur.next.left;
            cur = cur.next;
        }
        copyRoot = copyRoot.left;
    }
    return root;
}
```
{% endtab %}
{% endtabs %}

