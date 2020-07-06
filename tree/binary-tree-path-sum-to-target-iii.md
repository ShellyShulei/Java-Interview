# Binary Tree Path Sum To Target III

Given a binary tree in which each node contains an integer number. Determine if there exists a path **\(the path can only be from one node to itself or to any of its descendants\),** the sum of the numbers on the path is the given target number.

```text
Examples
    5
  /    \
2      11
     /    \
    6     14
  /
 3
```

If target = 17, There exists a path 11 + 6, the sum of the path is target.

If target = 10, There does not exist any paths sum of which is target.

If target = 11, There exists a path only containing the node 11.

```text
public class Solution {
  public boolean exist(TreeNode root, int target) {
    if (root == null) {
      return false;
    }
    List<TreeNode> path = new LinkedList<>();
    return helper(root, path, target);
  }
  private boolean helper(TreeNode root, List<TreeNode> path, int target) {
    path.add(root);
    int tmp = 0;
    for(int i = path.size()-1; i>=0; i--) {
      tmp += path.get(i).key;
      if (tmp == target){
        return true;
      }
    }
    if (root.left != null && helper(root.left, path, target)) {
      return true;
    }
     if (root.right != null && helper(root.right, path, target)) {
      return true;
    }
    path.remove(path.size()-1);
    return false;
  }
}
```

{% hint style="info" %}
**437. 路径总和 III   算count**
{% endhint %}

则需要HashMap

若到结点B的路径和为currSum, 若存在A到B的路径和为target的话, 那一定存在 currSum-target的路径和

```text
class Solution {
    int count = 0;
    public int pathSum(TreeNode root, int sum) {
        if (root == null) {
            return count;
        }
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0,1);
        helper(root, 0, sum, map);
        return count;
    }
    private void helper(TreeNode root, int presum, int target, HashMap<Integer, Integer> map) {
        int sum =presum + root.val;
        if (map.containsKey(sum - target)) {
            count+= map.get(sum - target);
        }
        map.put(sum, map.getOrDefault(sum,0)+1);
        if (root.left != null) {
            helper(root.left, sum, target, map);
        }
         if (root.right != null) {
            helper(root.right, sum, target, map);
        }
         map.put(sum, map.getOrDefault(sum,0)-1);
    }
}
```



