### Solution

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node prev;
    public Node next;
    public Node child;
};
*/

class Solution {
    public Node flatten(Node head) {
        traverse(head);
        return head;
    }
    
    public Node traverse(Node node) {
        Node curr, prev, tail;
        curr = prev = node;
        while (curr != null) {
            if (curr.child == null) {
                prev = curr;
                curr = curr.next;
            }
            else {
                tail = traverse(curr.child);
                tail.next = curr.next;
                if (curr.next != null) curr.next.prev = tail;
                curr.next = curr.child;
                curr.child.prev = curr;
                curr.child = null;
                curr = tail.next;
                if (curr == null) prev = tail;
            }
        }
        return prev;
    }        
}
```

### Time/Space Compelxity

- Time Compelxity: O(nodes)
- Space Compelxity: O(levels)
