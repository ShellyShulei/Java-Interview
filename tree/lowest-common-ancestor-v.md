# Lowest Common Ancestor V

Given two nodes in a K-nary tree, find their lowest common ancestor.

Assumptions

-There is no parent pointer for the nodes in the K-nary tree.

-The given two nodes are guaranteed to be in the K-nary tree.

Examples

        5

      /   \

     9   12

   / \| \      \

 1 2   3      14

The lowest common ancestor of 2 and 14 is 5.

The lowest common ancestor of 2 and 9 is 9.

Case 1: if all of them are null, return null

Case 2: if one of them is not null, return non-null node

Case 3: if more than one of them are not null, return root;

```text
/**
 * public class KnaryTreeNode {
 *     int key;
 *     List<KnaryTreeNode> children;
 *     public KnaryTreeNode(int key) {
 *         this.key = key;
 *         this.children = new ArrayList<>();
 *     }
 * }
 */
public class Solution {
  public KnaryTreeNode lowestCommonAncestor(KnaryTreeNode root, KnaryTreeNode a, KnaryTreeNode b) {
    if (root == null || root == a || root == b) {
      return root;
    }
   KnaryTreeNode found = null;
    for (KnaryTreeNode child : root.children) {
      KnaryTreeNode common = lowestCommonAncestor(child, a, b);
      if (common != null) {
        if (found == null) {
          found = common;
        } else {
          return root;
        }
      }
    }
    return found;
  }
}
```



