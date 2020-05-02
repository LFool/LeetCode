# Binary Tree Postorder Traversal

Given a binary tree, return the _postorder_ traversal of its nodes' values.

**Example:**

```text
Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [3,2,1]
```

**Follow up:** Recursive solution is trivial, could you do it iteratively?

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        Stack<TreeNode> stack = new Stack<>();

        while(root != null || !stack.isEmpty()) {
            // find leaf nodes
            while (root != null) {
                stack.push(root);
                if (root.left != null) {
                    root = root.left;
                } else {
                    root = root.right;
                }
            }
            TreeNode node = stack.pop();
            list.add(node.val);
            if (!stack.isEmpty() && stack.peek().left == node) {
                root = stack.peek().right;
            }
        }

        return list;
    }
}
```

