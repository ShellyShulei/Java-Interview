# 103. Binary Tree Zigzag Level Order Traversal



Given a binary tree, return the zigzag level order traversal of its nodes' values. \(ie, from left to right, then right to left for the next level and alternate between\).

For example:  
Given binary tree `[3,9,20,null,null,15,7]`

```text
    3
   / \
  9  20
    /  \
   15   7
```

return its zigzag level order traversal as:

```text
[
  [3],
  [20,9],
  [15,7]
]
```

Solution: 用Deque

```text
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        Deque<TreeNode> deque = new LinkedList<TreeNode>();
        int layer = 0;
        deque.offerFirst(root);
        while (!deque.isEmpty()) {
            int size = deque.size();
            List<Integer> curlayer = new LinkedList<>();
            for (int i = 0; i<size; i++) {
                if (layer == 0) {
                  TreeNode cur = deque.pollFirst();
                  curlayer.add(cur.val);
                  if (cur.left != null) {
                      deque.offerLast(cur.left);
                  }
                  if (cur.right!= null) {
                      deque.offerLast(cur.right);
                  }
                }
                if (layer == 1) {
                  TreeNode cur = deque.pollLast();
                  curlayer.add(cur.val);
                  if (cur.right != null) {
                      deque.offerFirst(cur.right);
                  }
                  if (cur.left!= null) {
                      deque.offerFirst(cur.left);
                  }
                }
          }
          result.add(curlayer); 
          layer = 1-layer;         
        }
     return result;
    }
}
```



从左往右的话 pollFirst\(\) 先左后右offerLast\(\)

从右往左 pollLast\(\) 先右后左 offerFirst\(\);

Time: O\(n\)  

Space: O\(n\)



