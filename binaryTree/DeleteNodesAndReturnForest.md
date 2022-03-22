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
    
    int [] toDeleteNodes;
    TreeNode dummyRoot;
    List<TreeNode> forest;
    
    public List<TreeNode> delNodes(TreeNode root, int [] to_delete) {
        forest = new ArrayList<>();
        dummyRoot = new TreeNode(0, root, null);
        toDeleteNodes = new int [1000];
        for (int nodeToDelete : to_delete)
            toDeleteNodes[nodeToDelete - 1]++;
        getForest(root, dummyRoot);
        if (dummyRoot.left != null) forest.add(dummyRoot.left);
        return forest;
    }
    
    public void getForest(TreeNode node, TreeNode parent) {
        if (node == null) return;
        getForest(node.left, node);
        getForest(node.right, node);
        if (toDeleteNodes[node.val - 1] == 1) {
            if (node.left != null) forest.add(node.left);
            if (node.right != null) forest.add(node.right);
            if (parent.left == node) parent.left = null;
            else parent.right = null;
            toDeleteNodes[node.val - 1]--;
        }
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
