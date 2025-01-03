# Tree Patterns

## Theory
- The number of nodes in a full binary tree can never be a power of 2, as the first node is just 1

## Tree Memoisation based pattern  
- In some problems, we need to do some memoisation so that we do not have to run recursion for children at every parent node
- In such use-cases, create an object and pass that around in the recursive calls
- If its a global state, then use a static variable, if its local to a certain recursion, use java class object
- eg1: Check whether tree is height-balanced or not, here we need to return boolean
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
- eg2: Diameter of tree, here we need to again store heights at each node
- eg3: Max path sum: store the sums of the sub-trees

## Horizontal distance pattern (HD pattern)
- Horizontal Distance from the root of the tree
- Can be computed using a queue
```java
class TreeNode{
  Node node;
  int hd;

  TreeNode(Node node){
    this.node = node;
  }

  TreeNode(Node node, int hd){
   this.node = node;
   this.height = height;
 }
}

Queue<TreeNode> queue = new LinkedList<>();
queue.add(new TreeNode(root));

while(!queue.isEmpty()){
  TreeNode temp = queue.poll();
  if(temp.node.left != null){
    queue.add(new TreeNode(temp.node.left, temp.node.height-1));
 }
 if(temp.node.right != null){
  queue.add(new TreeNode(temp.node.right, temp.node.height+1));
 }
}
```

## Traversal patterns
- Inorder: left -> parent -> right (recursion)
- Preorder: parent -> left -> right (recursion)
- Postorder: left -> right -> parent (recursion)
- Level order: Traverse every level , use queue DS
- ZigZag: use 2 stacks with a flag to indicate direction
- Vertical: Use horizontal distance pattern
- Boundary: traverse left boundary, traverse leaf nodes, traverse right boundary, do not use HD pattern, rather use a linkedhashSet to make sure the same node is not processed twice in output

## View Patterns
- Top:  horizontal distance pattern + level order traversal: pick the first element in level order traversal for a given horizontal distance
- Left: level order traversal
- Right: level order traversal
- Bottom: horizontal distance pattern + level order traversal: pick the last element in level order traversal for a given horizontal distance

## Neighbors of node in binary tree
- The left and right nodes and the parent node are considered neigbors of a node in binary tree
- The left and right are easily available from the node structure
- To get the parent, create a child to parent map
```java
private static void populateChildToParentMap(Node root,Node parent, Map<Node, Node> childToParentMap){
      if(root == null){
          return;
      }  
      childToParentMap.put(root,parent);
      populateChildToParentMap(root.left, root,childToParentMap);
      populateChildToParentMap(root.right, root,childToParentMap);
      
    }

```

## Tree construction from traversals
- Preorder 0 to length-1 arrangement always points to the root , then root of left, then root of right
- Postorder length-1 to 0 arrangement always points to the root, root of right , then root of left
- InOrder helps to identify what elements lie to the left and right of the root

 ```java
private static Node buildTree(int[] inorder, int[] preorder,Index index, int low, int high){
        if(high<low){
            return null;
        }
       int rootLocation = find(inorder, preorder[index.value]);
       if(rootLocation >= low && rootLocation <=high){
           Node root = new Node(preorder[index.value]);
           index.value++;
           root.left = buildTree(inorder, preorder,index,low,rootLocation-1);
           root.right = buildTree(inorder, preorder,index,rootLocation+1, high);
           return root;
          
       }
       return null;
    }
``` 

