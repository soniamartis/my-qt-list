# Leetcode 150 problems

https://leetcode.com/studyplan/top-interview-150/

## Merge array
- Merge needs to happen inplace w/o using an additional temp array
- Hence, exploit the fact, that since the arrays are sorted, instead of comparing from the startIndexes, compare from the endIndexes
```java
    public void merge(int[] nums1, int m, int[] nums2, int n) {
       int i = m -1;
       int j = n -1;
       int position = nums1.length-1;
       while(i>=0 && j>=0){
        if(nums1[i] <= nums2[j]){
            nums1[position--] = nums2[j--];
        }
        else{
            nums1[position--] = nums1[i--];
        }
       }
       while(i>=0){
        nums1[position--] = nums1[i--];
       }
       while(j>=0){
        nums1[position--] = nums2[j--];
       }
    }
```

## Min absolute diff in BST
- In BST, min diff is just the diff between the nodes in inorder traversal
```java
private void inorder(TreeNode root){
        if(root != null){
            inorder(root.left);
            if(prev !=null && root.val - prev.val < minDiff){
                minDiff = root.val - prev.val;
            }
            prev = root;
            inorder(root.right);
        }
    }
```
