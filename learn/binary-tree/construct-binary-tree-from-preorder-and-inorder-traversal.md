# Construct Binary Tree from Preorder and Inorder Traversal

Given preorder and inorder traversal of a tree, construct the binary tree.

**Note:**  
You may assume that duplicates do not exist in the tree.

For example, given

> **preorder** = \[3,9,20,15,7\] 
>
> **inorder** = \[9,3,15,20,7\]

Return the following binary tree:

```text
    3
   / \
  9  20
    /  \
   15   7
```

\*\*\*\*

**Solution Code:**

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
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if (preorder == null || inorder == null || preorder.length != inorder.length) {
            return null;
        }
        Map<Integer, Integer> hm = new HashMap<>();
        for (int i = 0; i < inorder.length; i++) {
            hm.put(inorder[i], i);
        }
        return buildTree(preorder, 0, preorder.length - 1, hm, 0, inorder.length - 1);
    }
    public TreeNode buildTree(int[] preorder, int pb, int pe, Map<Integer, Integer> hm, int ib, int ie) {
        if (pb > pe || ib > ie) {
            return null;
        }
        TreeNode root = new TreeNode(preorder[pb]);
        int ci = hm.get(preorder[pb]);
        
        root.left = buildTree(preorder, pb + 1, pb + ci - ib, hm, ib, ci - 1);
        root.right = buildTree(preorder, pb + ci - ib + 1, pe, hm, ci + 1, ie);
        return root;
    }
}
```

