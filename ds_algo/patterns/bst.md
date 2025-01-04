# Binary Search Tree

## NOTES
### Inorder traversal pattern
- Inorder traversal yields an array that is in sorted order
- We can exploit this property to find min, max, kth smallest element just by doing inorder traversal
- To find the predecessor of every node, we use below algorithm:
```java
private void inorder(TreeNode root){
        if(root != null){
            inorder(root.left);
            //some logic
            if(prev !=null && root.val - prev.val < minDiff){
                minDiff = root.val - prev.val;
            }
            prev = root;
            inorder(root.right);
        }
    }
```

### Range check pattern
- Useful for validating whether a tree is BST or not
```java
    public boolean isValidBST(TreeNode root) {
       return isValidBST(root, Long.MIN_VALUE, Long.MAX_VALUE); 
    }

    private boolean isValidBST(TreeNode root, long min, long max){
        if(root == null){
            return true;
        }
        return root.val > min  && root.val < max && isValidBST(root.left, min , root.val ) && isValidBST(root.right, root.val , max);
    }
```

