# Maximum Path Sum Binary Tree II

Given a binary tree in which each node contains an integer number. Find the maximum possible sum **from any node to any node \(the start node and the end node can be the same\).** 

**Assumptions**

* ​The root of the given binary tree is not null

**Examples**

   -1

  /    \

2      11

     /    \

    6    -14

one example of paths could be -14 -&gt; 11 -&gt; -1 -&gt; 2

another example could be the node 11 itself

The maximum path sum in the above binary tree is 6 + 11 + \(-1\) + 2 = 18

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
    int left = helper (root.left);
    int right = helper(root.right);
    left = left < 0 ? 0: left;
    right = right < 0 ? 0 : right;
    max = Math.max(max, root.key + left + right);
    return Math.max(left, right) + root.key;
  }
}
```



