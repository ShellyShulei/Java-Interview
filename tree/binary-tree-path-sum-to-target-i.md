# 112. Binary Tree Path Sum To Target I

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

For example: Given the below binary tree and `sum = 22`,

```text
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
```

return true, as there exist**s** a root-to-leaf path`5->4->11->2`which sum is 22.

```text
  public boolean hasPathSum(TreeNode root, int sum) {
        if (root == null) {
            return false;
        }
        if (root.left == null && root.right == null) {
            if (root.val == sum) {
                return true;
            } else {
                return false;
            }
        }
        return hasPathSum(root.left, sum - root.val) || hasPathSum(root.right, sum - root.val);
    }
```

Time: O\(n\)

Space: worst is O\(n\)  if tree is balanced, O\(logn\)

