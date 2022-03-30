### Solution

```java
class BrowserHistory {

    static class WebsiteNode {
        String name;
        int pos;
        WebsiteNode next;
        
        public WebsiteNode(String name, int pos) {
            this.name = name;
            this.pos = pos;
        }
    }
    
    WebsiteNode curr;
    Map<Integer, WebsiteNode> websites;
    int size;
        
    public BrowserHistory(String homepage) {
        this.curr = new WebsiteNode(homepage, 0);
        this.websites = new HashMap<>();
        this.websites.put(0, curr);
        this.size = 1;
    }
    
    public void visit(String url) {
        curr.next = new WebsiteNode(url, curr.pos + 1);
        curr = curr.next;
        websites.put(curr.pos, curr);
        size = curr.pos + 1;
    }
    
    public String back(int steps) {
        int backPos = Math.max(0, curr.pos - steps);
        curr = websites.get(backPos);
        return curr.name;
    }
    
    public String forward(int steps) {
        int forwardPos = Math.min(size - 1, curr.pos + steps);
        curr = websites.get(forwardPos);
        return curr.name;
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * BrowserHistory obj = new BrowserHistory(homepage);
 * obj.visit(url);
 * String param_2 = obj.back(steps);
 * String param_3 = obj.forward(steps);
 */
 ```
