# Lowest Common Ancestor IV

Given K nodes in a binary tree, find their lowest common ancestor.

**Assumptions**

* K &gt;= 2
* There is **no** parent pointer for the nodes in the binary tree
* The given K nodes are **guaranteed** to be in the binary tree

**Examples**

        5

      /   \

     9     12

   /  \      \

  2    3      14

The lowest common ancestor of 2, 3, 14 is 5

The lowest common ancestor of 2, 3, 9 is 9



用HashSet把TreeNode都保存下来

```text
/**
 * public class TreeNode {
 *   public int key;
 *   public TreeNode left;
 *   public TreeNode right;
 *   public TreeNode(int key) {
 *     this.key = key;
 *   }
 * }
 */
public class Solution {
  public TreeNode lowestCommonAncestor(TreeNode root, List<TreeNode> nodes) {
    Set<TreeNode> set = new HashSet<>(nodes);
    return helper(set, root);
  }
  private TreeNode helper(Set<TreeNode> set, TreeNode root) {
    if (root == null) {
      return root;
    }
    if (set.contains(root)) {
      return root;
    }
    TreeNode left = helper(set,root.left);
    TreeNode right = helper(set, root.right);
    if (left != null && right != null) {
      return root;
    }
    return left == null? right: left;
  }
}
```

