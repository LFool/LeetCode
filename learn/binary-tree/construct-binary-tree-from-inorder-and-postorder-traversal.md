# Construct Binary Tree from Inorder and Postorder Traversal

Given inorder and postorder traversal of a tree, construct the binary tree.

**Note:**  
You may assume that duplicates do not exist in the tree.

For example, given

> **inorder** = \[9,3,15,20,7\] 
>
> **postorder** = \[9,15,7,20,3\]

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
public TreeNode buildTree(int[] inorder, int[] postorder) {
    if (inorder == null || postorder == null || inorder.length != postorder.length) {
        return null;
    }
    // 将 inorder[] 的值和下标形成映射
    Map<Integer, Integer> hm = new HashMap<>();
    for (int i = 0; i < inorder.length; i++) {
        hm.put(inorder[i], i);
    }
    return buildTree(hm, 0, inorder.length - 1, postorder, 0, postorder.length - 1);
}

/**
 * inorder 的作用是划分 postorder 中的左右子树的区间，此处用 hm 代替
 * 当从 postorder 中获取到root节点后，通过 inorder 划分剩下的区间
 * 参数说明：
 *          ib -> inorderBeginIndex
 *          ie -> inorderEndIndex
 *          pb -> postorderBeginIndex
 *          pe -> postorderEndIndex
 */
public TreeNode buildTree(Map<Integer, Integer> hm, int ib, int ie, int[] postorder, int pb, int pe) {
    if (ib > ie || pb > pe) {
        return null;
    }
    TreeNode root = new TreeNode(postorder[pe]);
    int index = hm.get(postorder[pe]);
    root.left = buildTree(hm, ib, index - 1, postorder, pb, pb + index - ib - 1);
    root.right = buildTree(hm, index + 1, ie, postorder, pb + index - ib, pe - 1);
    return root;
}
```

