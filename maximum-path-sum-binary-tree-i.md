# Maximum Path Sum Binary Tree I

Given a binary tree in which each node contains an integer number. Find the maximum possible sum **from one leaf node to another leaf node.** If there is no such path available, return Integer.MIN\_VALUE\(Java\)/INT\_MIN \(C++\).

**Examples**

  -15

  /    \

2      11

     /    \

    6     14

The maximum path sum is 6 + 11 + 14 = 31.

只有当左右子节点都不为空时， 才更新max

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
    if (root == null || root.left == null || root.right == null) {
      return max;
    }
    helper(root);
    return max;
  }
  private int helper (TreeNode root) {
    if (root == null) {
      return 0;
    }
    int left = helper(root.left);
    int right = helper(root.right);
     while (root.left != null && root.right != null) {
      int sum = left + right + root.key;
      max = Math.max(max, sum);
      return root.key+ Math.max(left,right);
    }
    return root.left == null? right+root.key : left + root.key;
  }
}
```



