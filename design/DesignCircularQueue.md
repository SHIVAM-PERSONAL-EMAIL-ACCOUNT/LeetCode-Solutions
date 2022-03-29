### Solution

```java
class MyCircularQueue {
    
    static class Node {
        int val;
        Node next;
        
        public Node(int val) {
            this.val = val;
        }
        
        public Node(int val, Node next) {
            this.val = val;
            this.next = next;
        }
    }
    
    Node qnode;
    Node front;
    Node rear;
    int capacity;
    int size;
    
    public MyCircularQueue(int capacity) {
        this.qnode = this.front = this.rear = null;
        this.size = 0;
        this.capacity = capacity;
    }
    
    public boolean enQueue(int value) {
        if (size == capacity) return false;
        if (size == 0) {
            qnode = new Node(value);
            front = rear = qnode;
        }
        else {
            rear.next = new Node(value);
            rear = rear.next;
        }
        size = size + 1;
        return true;
    }
    
    public boolean deQueue() {
        if (size == 0) return false;
        if (size == 1) {
            qnode = front = rear = null;
        }
        else {
            front = front.next;
        }
        size = size - 1;
        return true;
    }
    
    public int Front() {
        if (front == null) return -1;
        return front.val;
    }
    
    public int Rear() {
        if (rear == null) return -1;
        return rear.val;
    }
    
    public boolean isEmpty() {
        return size == 0;
    }
    
    public boolean isFull() {
        return size == capacity;
    }
}

/**
 * Your MyCircularQueue object will be instantiated and called as such:
 * MyCircularQueue obj = new MyCircularQueue(k);
 * boolean param_1 = obj.enQueue(value);
 * boolean param_2 = obj.deQueue();
 * int param_3 = obj.Front();
 * int param_4 = obj.Rear();
 * boolean param_5 = obj.isEmpty();
 * boolean param_6 = obj.isFull();
 */
 ```
