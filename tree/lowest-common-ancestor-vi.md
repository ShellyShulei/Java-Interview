# Lowest Common Ancestor VI

Given M nodes in a K-nary tree, find their lowest common ancestor.

Assumptions

- M &gt;= 2.

- There is no parent pointer for the nodes in the K-nary tree.

- The given M nodes are guaranteed to be in the K-nary tree.

Examples

        5  


      /   \

     9   12

   / \| \      \

  1 2 3     14

The lowest common ancestor of 2, 3, 14 is 5.

The lowest common ancestor of 2, 3, 9 is 9.

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
  public KnaryTreeNode lowestCommonAncestor(KnaryTreeNode root, List<KnaryTreeNode> nodes) {
    Set<KnaryTreeNode> set = new HashSet<>(nodes);
    return helper(root, set);
  }
  private KnaryTreeNode helper(KnaryTreeNode root, Set<KnaryTreeNode> set) {
    if (root == null || set.contains(root)) {
      return root;
    }
    KnaryTreeNode found = null;
    for (KnaryTreeNode child: root.children) {
      KnaryTreeNode node = helper(child, set);
      if (node != null) {
        if (found == null) {
          found = node;
        } else {
          return root;
        }
      }
    }
    return found;
  }
}
```



