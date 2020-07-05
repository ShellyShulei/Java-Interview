# Max Path Sum From Leaf To Root

Given a binary tree in which each node contains an integer number. Find the maximum possible path sum from a leaf to root.

Assumptions

The root of the given binary tree is not null.

Examples

```text
          10
       /      \
    -2        7
  /     \
8      -4
```

        

The maximum path sum is 10 + 7 = 17.

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
  public int maxPathSumLeafToRoot(TreeNode root) {
    int sum = 0;
    return maxSum(root,sum);
  }
  public int maxSum(TreeNode root, int sum) {
    sum += root.key;
    if (root.left == null && root.right == null) {
      return sum;
    } else if (root.left == null) {
      return maxSum(root.right, sum);
    }else if (root.right == null){
      return maxSum(root.left, sum);
    }
     return Math.max(maxSum(root.left,sum), maxSum(root.right,sum));
  }
}
```



