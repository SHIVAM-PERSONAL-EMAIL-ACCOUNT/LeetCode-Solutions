### Solution

```java
class CustomStack {

    int [] stack;
    int [] increment;
    int counter;
    
    public CustomStack(int maxSize) {
        stack = new int [maxSize];
        increment = new int [maxSize];
        counter = -1;
    }
    
    public void push(int x) {
        if (counter != stack.length - 1)
            stack[++counter] = x;
    }
    
    public int pop() {
        if (counter == -1) return -1;
        int ele = stack[counter] + increment[counter];
        stack[counter] = 0;
        if (counter > 0) increment[counter - 1] += increment[counter] ;
        increment[counter] = 0;
        --counter;
        return ele;
    }
    
    public void increment(int k, int val) {
        if (counter != -1) 
            increment[Math.min(k - 1, counter)] += val;
    }
}

/**
 * Your CustomStack object will be instantiated and called as such:
 * CustomStack obj = new CustomStack(maxSize);
 * obj.push(x);
 * int param_2 = obj.pop();
 * obj.increment(k,val);
 */
 ```
 
 ### Time/Space Complexity
 
 - Time Complexity: O(1)
 - Space Complexity: O(n)
