### Solution

```java
class Solution {
    
    
    public int longestSubarray(int [] nums, int limit) {
        Queue<Integer> minHeap = new PriorityQueue<>();   
        Queue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());  
        
        int i, size, j, window;

        minHeap.offer(nums[0]);
        maxHeap.offer(nums[0]);
        size = nums.length;
        window = 1;
        i = j = 0;
        while (i < size) {
            int diff = Math.abs(minHeap.peek() - maxHeap.peek());
            if (diff <= limit) {
                window = Math.max(window, i - j + 1);
                i++;
                if (i == size) 
                    break;
                minHeap.offer(nums[i]);
                maxHeap.offer(nums[i]);
            }
            else {
                minHeap.remove(nums[j]);
                maxHeap.remove(nums[j]);
                j++;
            }
        }
        
        return window;
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(n log n)
- Space Compelxity: O(n)
