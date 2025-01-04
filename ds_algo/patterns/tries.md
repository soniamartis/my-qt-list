# Tries

## Trie DS
```java
class TrieNode {
    TrieNode[] links = new TrieNode[26];
    boolean isComplete = false;

    public boolean contains(char ch){
        return links[ch-'a'] != null;
    }

    public TrieNode get(char ch){
        return links[ch-'a'];
    }

    public TrieNode add(char ch){
        TrieNode node = new TrieNode();
        links[ch-'a'] = node;
        return node;
    }

    public boolean isWordFound(){
        return isComplete;
    }
}

class Trie {

    TrieNode root;

    public Trie() {
       root = new TrieNode(); 
    }
    
    public void insert(String word) {
        char[] arr = word.toCharArray();
        TrieNode node = root;
        for(int i=0;i<arr.length; i++){
            if(node.contains(arr[i])){
                node = node.get(arr[i]);
            }
            else{
                node = node.add(arr[i]);
            }
        }
        node.isComplete = true;
    }
    
    public boolean search(String word) {
       TrieNode node = root;
       char []arr = word.toCharArray();
       for(int i=0;i<arr.length;i++){
        if(node.contains(arr[i])){
            node = node.get(arr[i]);
        }
        else return false;
       } 
       return node.isWordFound();
    }
    
    public boolean startsWith(String prefix) {
       TrieNode node = root;
       char []arr = prefix.toCharArray();
       for(int i=0;i<arr.length;i++){
        if(node.contains(arr[i])){
            node = node.get(arr[i]);
        }
        else return false;
       }  
       return node != null;
    }
}

```
