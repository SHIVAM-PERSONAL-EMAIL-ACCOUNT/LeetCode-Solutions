### Solution

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    
    public boolean findTarget(TreeNode root, int k) {
        List<Integer> nodes = new ArrayList<>();
        getNodes(root, nodes);
        int i = 0, j = nodes.size() - 1;
        while (i < j) {
            int sum = nodes.get(i) + nodes.get(j);
            if (sum == k) return true;
            else if (sum < k) i++;
            else j--;
        }
        return false;
    }
    
    public void getNodes(TreeNode node, List<Integer> nodes) {
        if (node == null) return;
        getNodes(node.left, nodes);
        nodes.add(node.val);
        getNodes(node.right, nodes);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
