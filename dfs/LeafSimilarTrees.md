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
    
    public boolean leafSimilar(TreeNode root1, TreeNode root2) {
        List<Integer> list1 = new ArrayList<>();
        List<Integer> list2 = new ArrayList<>();
        traverse(root1, list1);
        traverse(root2, list2);
        for (int i = 0; i < list1.size() && i < list2.size(); i++)
            if (list1.get(i) != list2.get(i)) 
                return false; 
        return list1.size() == list2.size();
    }
    
    public void traverse(TreeNode node, List<Integer> list) {
        if (node == null) return;
        
        if (node.left == null && node.right == null) {
            list.add(node.val);
            return;
        }
        
        traverse(node.left, list);
        traverse(node.right, list);
    }
}
```


### Time/Space Complexity

- Time Complexity: O(n)
- Space Compleixty: O(n)
