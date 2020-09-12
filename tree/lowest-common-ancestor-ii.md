# Lowest Common Ancestor II

Given two nodes in a binary tree \(with parent pointer available\), find their lowest common ancestor.

**Assumptions**

* There is _**parent**_ pointer for the nodes in the binary tree
* The given two nodes _**are not guaranteed**_ to be in the binary tree

**Examples**

        5

      /   \

     9     12

   /  \      \

  2    3      14

The lowest common ancestor of 2 and 14 is 5

The lowest common ancestor of 2 and 8 is null \(8 is not in the tree\)

Solution 1:

Time: O\(n\)  Space: O\(n\)

```text
/**
 * public class TreeNodeP {
 *   public int key;
 *   public TreeNodeP left;
 *   public TreeNodeP right;
 *   public TreeNodeP parent;
 *   public TreeNodeP(int key, TreeNodeP parent) {
 *     this.key = key;
 *     this.parent = parent;
 *   }
 * }
 */
public class Solution {
  public TreeNodeP lowestCommonAncestor(TreeNodeP one, TreeNodeP two) {
    Set<TreeNodeP> set = new HashSet<>();
    while (one != null && two != null) {
      if (set.contains(one)) {
        return one;
      }
      set.add(one);
      one = one.parent;
      if (set.contains(two)) {
        return two;
      }
      set.add(two);
      two = two.parent;
    }
    while (one != null) {
      if (set.contains(one)) {
        return one;
      } 
      set.add(one);
      one = one.parent;
    }
     while (two != null) {
      if (set.contains(two)) {
        return two;
      } 
      set.add(two);
      two = two.parent;
    }
    return null;
  }
}
```

Solution 2:

Time: O\(height\)   Space: O\(1\)

Step1: find depth\(a\) and depth\(b\)

Step2: form longer one, move \|depth\(a\) - depth\(b\)\|

Step3: move a and b together one step by one step, until a == b

```text
/**
 * public class TreeNodeP {
 *   public int key;
 *   public TreeNodeP left;
 *   public TreeNodeP right;
 *   public TreeNodeP parent;
 *   public TreeNodeP(int key, TreeNodeP parent) {
 *     this.key = key;
 *     this.parent = parent;
 *   }
 * }
 */
public class Solution {
  public TreeNodeP lowestCommonAncestor(TreeNodeP one, TreeNodeP two) {
    int a = depth(one);
    int b = depth(two);
    if(a<=b) {
      return helper(one, two, b-a);
    } 
    return helper(two, one, a-b);
  }
  private int depth (TreeNodeP node) {
    int d = 0;
    while (node != null) {
      d++;
      node = node.parent;
    }
    return d;
  }
  private TreeNodeP helper (TreeNodeP shorter, TreeNodeP longer, int diff) {
    while (diff > 0) {
      longer = longer.parent;
      diff--;
    }
    while (shorter != longer) {
      shorter = shorter.parent;
      longer = longer.parent;
    }
    return longer;
  }
}
```







