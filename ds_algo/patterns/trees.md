# Tree Patterns

- The number of nodes in a full binary tree can never be a power of 2, as the first node is just 1
- In some problems, we need to return boolean but also do some memoisation so that we do not have to run recursion for children at every parent node
- In such use-cases, create an object and pass that around in the recursive calls
- If its a global state, then use a static variable, if its local to a certain recursion, use java class object
- eg: Check whether tree is height-balanced or not, here we need to return boolean
- For every node, we have to compute the height of left and right sub-trees, that will increase complexity to N^2 . We can rather memoise and store the heights of each node and propagate that value through the method args

 ```java
    class Height{
        int value = 0;
    }
    
    public boolean isBalanced(Node root) {
        // code here
        return isBalanced(root, new Height());
    }
    
    private boolean isBalanced(Node root, Height h){
       if(root==null){
           return true;
       } 
       
       Height leftHeight = new Height();
       Height rightHeight = new Height();
       
       boolean isLeftBalanced = isBalanced(root.left,leftHeight);
       boolean isRightBalanced = isBalanced(root.right,rightHeight);
       
       if(isLeftBalanced && isRightBalanced && Math.abs(leftHeight.value-rightHeight.value)<=1){
           h.value = Math.max(leftHeight.value, rightHeight.value)+1;
           return true;
       }
       
       return false;
    }
``` 
