# Cousins in Binary Tree

## Description

In a binary tree, the root node is at depth `0`, and children of each depth `k` node are at depth `k+1`.

Two nodes of a binary tree are _cousins_ if they have the same depth, but have **different parents**.

We are given the `root` of a binary tree with unique values, and the values `x` and `y` of two different nodes in the tree.

Return `true` if and only if the nodes corresponding to the values `x` and `y` are cousins.

**Example 1:**  
![](https://assets.leetcode.com/uploads/2019/02/12/q1248-01.png)

> **Input:** root = \[1,2,3,4\], x = 4, y = 3 
>
> **Output:** false

**Example 2:**  
![](https://assets.leetcode.com/uploads/2019/02/12/q1248-02.png)

> **Input:** root = \[1,2,3,null,4,null,5\], x = 5, y = 4 
>
> **Output:** true

**Example 3:**

![](https://assets.leetcode.com/uploads/2019/02/13/q1248-03.png)

> **Input:** root = \[1,2,3,null,4\], x = 2, y = 3 
>
> **Output:** false

**Note:**

1. The number of nodes in the tree will be between `2` and `100`.
2. Each node has a unique integer value from `1` to `100`.

## code

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    Map<Integer, Integer> depth;
    Map<Integer, TreeNode> parent;

    public boolean isCousins(TreeNode root, int x, int y) {
        depth = new HashMap();
        parent = new HashMap();
        dfs(root, null);
        return (depth.get(x) == depth.get(y) && parent.get(x) != parent.get(y));
    }

    public void dfs(TreeNode node, TreeNode par) {
        if (node != null) {
            depth.put(node.val, par != null ? 1 + depth.get(par.val) : 0);
            parent.put(node.val, par);
            dfs(node.left, node);
            dfs(node.right, node);
        }
    }
}
```

