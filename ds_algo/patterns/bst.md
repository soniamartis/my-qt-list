# Binary Search Tree

## NOTES
- Inorder traversal yields an array that is in sorted order
- We can exploit this property to find min, max, kth smallest element just by doing inorder traversal
- To find the predecessor of every node, we can use below pattern:
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
