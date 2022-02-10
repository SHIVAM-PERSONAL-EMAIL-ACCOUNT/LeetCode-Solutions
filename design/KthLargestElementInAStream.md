### Solution

```java
class KthLargest {

    PriorityQueue<Integer> kq = new PriorityQueue<>();
    int flag;
    
    public KthLargest(int k, int [] nums) {
        for (int num : nums) {
            kq.offer(num);
        }
        int i = nums.length - k;
        while (!kq.isEmpty() && i > 0) {
            kq.poll();
            --i;
        }
        flag = k;
    }
    
    public int add(int val) {
        kq.offer(val); 
        if (kq.size() > flag) kq.poll();
        return kq.peek();
    }
}

/**
 * Your KthLargest object will be instantiated and called as such:
 * KthLargest obj = new KthLargest(k, nums);
 * int param_1 = obj.add(val);
 */
```

### Time/Space Complexity

- Time Complexity: O(log k), for `add` method
- Space Complexity: O(k)
