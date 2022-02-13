### Solution

```java
class Solution {
    
    public int numSubarrayBoundedMax(int [] nums, int left, int right) {
        int i, size, count, res, firstIndexIncluded, lastIndexExcluded;
        size = nums.length;
        
        /*
        For 'lastIndexExcluded', consider such a case: [3,4,1,2], 1, 2
        Here, first two numbers are more than the right. So we cannot include
        them in any subarray. So, we set 'lastIndexExcluded' to last index where we
        found a number greater than right. When we come to 1, we will get its all
        possible subarrays but substract the ones which include numbers greater than
        right.
        
        For 'firstIndexIncluded', consider such a case: [1,2,3,4], 3, 4
        Here, first two numbers are less than the the left so they themselves cannot be included
        in any subarray but they can be part of subarray formed by numbers 3 and 4.
        'firstIndexIncluded' represents the the index from where we start to
        form the subarrays. For first two numbers, 'firstIndexIncluded' is going to negate the
        contribution of 'lastIndexExcluded' but for the third num, it is not going to have any effect.
        
        First better understanding, test using following cases other than the above two:
        [2,2,3,4], 0, 1
        [2,2,3,4], 6, 7
        [1,2,3,4], 1, 2
        [1,2,3,4,5,6], 3, 4
        */
        
        i = 0;
        res = 0;
        firstIndexIncluded = -1; 
        lastIndexExcluded = -1;
        while (i < size) {
            if (nums[i] > right) lastIndexExcluded = i;
            if (nums[i] >= left) firstIndexIncluded = i;
            res += (i - lastIndexExcluded);
            res -= (i - firstIndexIncluded);
            i++;
        }
        
        return res;
    }
}
```

### Time/Space Complexity

- Time Compleixty: O(n)
- Space Complexity: O(1)
