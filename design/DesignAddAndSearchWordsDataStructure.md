### Solution

```java
class WordDictionary {

    static class WordDepth {
        int [] present;
        WordDepth [] level;
        int [] ends;
        
        public WordDepth() {
            present = new int [26];
            level = new WordDepth [26];
            ends = new int [26];
        }
    }
    
    public WordDepth parent;
    
    public WordDictionary() {
        parent = new WordDepth();
    }
    
    public void addWord(String word) {
        addWordUtil(0, word.length(), word, parent);
    }
    
    public void addWordUtil(int index, int size, String word, WordDepth depth) {
        char alpha = word.charAt(index);
        int pos = alpha - 'a';
        if (depth.present[pos] == 0) depth.present[pos] = 1;
        if (index + 1 == size) {
            depth.ends[pos] = 1;
            return;
        }
        if (depth.level[pos] == null) depth.level[pos] = new WordDepth();
        addWordUtil(index + 1, size, word, depth.level[pos]);
    }
    
    public boolean search(String word) {
        return searchUtil(0, word.length(), word, parent);
    }
    
    public boolean searchUtil(int index, int size, String word, WordDepth depth) {
        if (depth == null) return false;
        char alpha = word.charAt(index);
        if (alpha == '.') {
            boolean res = false;
            for (int i = 0; i < 26; i++) {
                if (depth.present[i] == 1) {
                    if (index + 1 == size) {
                        if (depth.ends[i] == 1) return true;
                    }
                    else res = res || searchUtil(index + 1, size, word, depth.level[i]);
                }
            }
            return res;
        }
        else {
            int pos = alpha - 'a';
            if (depth.present[pos] == 0) return false;
            if (index + 1 == size) return depth.ends[pos] == 1;
            return searchUtil(index + 1, size, word, depth.level[pos]);
        }
    }
}

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary obj = new WordDictionary();
 * obj.addWord(word);
 * boolean param_2 = obj.search(word);
 */
 ```
 
 ### Time/Space Complexity
 
 - Time Complexity: O(n), where `n` is the length of the longest word (WORST CASE occurs when every character of the string is `.`)  
 - Space Complexity: O(n), where `n` is the length of the longest word
