### Solution

```java
class Trie {

    static class TrieNode {
        int [] alpha;
        int [] fullStop;
        TrieNode [] subTrieNodes;
        
        public TrieNode() {
            alpha = new int [26];
            fullStop = new int [26]; 
            subTrieNodes = new TrieNode [26];
        }
    }
    
    TrieNode root;
    
    public Trie() {
        root = new TrieNode();
    }
    
    public void insert(String word) {
        insertUtil(root, word, 0, word.length());
    }
    
    public void insertUtil(TrieNode node, String word, int index, int size) {
        if (index == size) return;
        char ch = word.charAt(index);
        node.alpha[ch - 'a'] = 1;
        if (index == size - 1) { node.fullStop[ch - 'a'] = 1; return; }
        if (node.subTrieNodes[ch - 'a'] == null) node.subTrieNodes[ch - 'a'] = new TrieNode();
        insertUtil(node.subTrieNodes[ch - 'a'], word, index + 1, size);
    }
    
    public boolean search(String word) {
        return searchUtil(root, word, 0, word.length());
    }
    
    public boolean searchUtil(TrieNode node, String word, int index, int size) {
        if (node == null) return false;
        char ch = word.charAt(index);
        if (node.alpha[ch - 'a'] != 1) return false;
        if (index == size - 1) return node.fullStop[ch - 'a'] == 1;
        return searchUtil(node.subTrieNodes[ch - 'a'], word, index + 1, size);
    }
    
    public boolean startsWith(String prefix) {
        return startsWithUtil(root, prefix, 0, prefix.length());
    }
    
    public boolean startsWithUtil(TrieNode node, String prefix, int index, int size) {
        if (index == size) return true;
        if (node == null) return false;
        char ch = prefix.charAt(index);
        if (node.alpha[ch - 'a'] != 1) return false;
        return startsWithUtil(node.subTrieNodes[ch - 'a'], prefix, index + 1, size);
    }
}

/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * boolean param_2 = obj.search(word);
 * boolean param_3 = obj.startsWith(prefix);
 */
 ```
 
 ### Time/Space Complexity
 
 - Time Complexity: O(n) where `n` is the length of the word
 - Space Complexity: O(n) where `n` is the length of the word
