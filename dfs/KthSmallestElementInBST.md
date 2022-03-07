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
    
    int ans = 0;
    int i = 1; // used to keep track of the distance of the element from the kth position
    
    public int kthSmallest(TreeNode root, int k) {
        dfs(root, k);
        return ans;
    }
    
    /*
    We perform In-Order Tree Traversal because we want to find the leftmost element of any given sub-tree
    */
    public void dfs(TreeNode node, int k) {
        if (node == null) 
            return;
        
        dfs(node.left, k);
        
        /*
        After i == k, we have got the required element. Now we don't need to check with other elements in the 
        tree. So we set i = k + 1 (Naturally Unacheivable condition) to exit the recursion
        */
        if (i == k + 1) return;
        
        /*
        If i == k, that means we have found the required element.
        So we set it to ans and set i = k + 1 so that after we have found the ans, we dont come back 
        to this condition again to overwrite the value of ans
        */
        if (i == k) {
            ans = node.val;
            i = k + 1;
            return;
        }
          
        /*
        If the answer wasn't found then i < k, so we increment i and search in the right sub-tree of the current tree
        */
        i++;
        dfs(node.right, k);
    }
}
```
### Time/Space Compelxity

- Time Compelxity: O(n)
- Space Compelxity: O(n), for a degenerate/unbalanced tree
