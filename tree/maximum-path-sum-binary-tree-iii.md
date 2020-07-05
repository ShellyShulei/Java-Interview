# Maximum Path Sum Binary Tree III

Given a binary tree in which each node contains an integer number. Find the maximum possible subpath sum**\(both the starting and ending node of the subpath should be on the same path from the root to one of the leaf nodes, and the subpath is allowed to contain only one node\).**

**Assumptions**

* The root of the given binary tree is not null

**Examples**

```text
    -5
  /    \
2      11
     /    \
    6     14
           /
        -3
```

The maximum path sum is 11 + 14 = 25

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
  int max = Integer.MIN_VALUE;
  public int maxPathSum(TreeNode root) {
    helper(root);
    return max;
  }
  private int helper (TreeNode root) {
    if (root == null) {
      return 0;
    }
    int left =helper(root.left);
    int right = helper(root.right);
    int sum = Math.max(Math.max(left,right), 0) + root.key;
    max = Math.max(max, sum);
    return sum;
  }
}
```


