# Tries

Tries also called, **digital tree** and sometimes **radix tree** or **prefix tree**. It is a DFA (Deterministic Finite Automation).

### Implementation of Word Dictionary

``` java
class Trie {
    
    static final char NULL = '\u0000';

    static class Node {
        char value;
        Node[] children;
        boolean isWord;
        Node(char value) {
            this.isWord = false;
            this.children = new Node[26];
            this.value = value;
        }
    }
    
    private Node root;
    
    /** Initialize your data structure here. */
    public Trie() {
        root = new Node(NULL);
    }
    
    private Node addChild(Node parent, char value) {
        Node child = parent.children[value-'a'];
        if(child == null) {
            child = new Node(value);
            parent.children[value-'a'] = child;
        }
        return child;
    }
    
    /** Inserts a word into the trie. */
    public void insert(String word) {
        Node node = this.root;
        for(int i = 0; i < word.length(); i++) {
            char cur = word.charAt(i);
            node = addChild(node, cur);
        }
        node.isWord = true;
    }
    
    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        Node node = this.root;
        for(int i = 0; i < word.length(); i++) {
            char cur = word.charAt(i);
            node = node.children[cur-'a'];
            if(node == null) {
                return false;
            }
        }
        return node.isWord;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        Node node = this.root;
        for(int i = 0; i < prefix.length(); i++) {
            char cur = prefix.charAt(i);
            node = node.children[cur-'a'];
            if(node == null) {
                return false;
            }
        }
        boolean exactMatch = node.value == prefix.charAt(prefix.length()-1);
        return node.children.length > 0 || exactMatch;
    }
}
```