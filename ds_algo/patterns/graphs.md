# Graphs

## Notes
- In both graph traversals BFS and DFS, we need to maintain visited array to make sure we are not visiting the same node twice, esp. for undirected graphs
- In BFS, check visited before adding to queue, in DFS, check visited before adding to recursion stack
- In flood-fill/ dfs, if we are updating the input matrix inplace with a new color, that itself serves as a visited, so no new visited is required.
- If we cannot update in-place, then visited will be required

### BFS Pattern
- Best for finding nodes closest from root
- Goes level by level

```java
 ArrayList<Integer> out = new ArrayList<>();
        Queue<Integer> queue = new LinkedList<>();
        boolean []visited = new boolean[V];
        queue.add(0);
        visited[0] = true;
        while(!queue.isEmpty()){
            Integer u = queue.poll();
            out.add(u);
            for(Integer v: adj.get(u)){
                if(!visited[v]){
                    visited[v] = true;
                    queue.add(v);
                }
            }
        }
```  

### DFS Pattern
- Goes path by path, where path = path from root to leaf

```java
private void dfs(int u,ArrayList<ArrayList<Integer>> adj, Set<Integer> visited, ArrayList<Integer> out){
        visited.add(u);
        out.add(u);
        for(Integer v: adj.get(u)){
            if(!visited.contains(v)){
                dfs(v,adj,visited,out);
            }
        }
}
```

### Find 4 adjacent neighbors in matrix
```java
int [][]directions = {{0,-1},{-1,0},{0,1},{1,0}}; // W, N, E, S
for(int[] dir: directions){
  int i = pos.i + dir[0];
  int j = pos.j + dir[1];
}
```

### Find 8 adjacent neighbors in matrix
```java
int [][]directions = {{-1,-1},{-1,0},{-1,1},{0,-1},{0,1},{1,-1},{1,0},{1,1}}; // top row, current row, bottom row
for(int[] dir: directions){
  int i = pos.i + dir[0];
  int j = pos.j + dir[1];
}
```

### Cycle detection in directed graph
- There is a cycle in directed graph if there is a back-edge, ie, an edge from current node to ancestor node
- This means, if the recursion stack contains the ancestor node while running dfs, a cycle is found
- Here visited is just used to track whether all disjoint components are visited or not, and is not used for cycle detection
- For cycle detection, we use a separate set that contains nodes that were visited in the current dfs

```java
private boolean dfs(int u, ArrayList<ArrayList<Integer>> adj,boolean [] visited,Set<Integer> stack){
        visited[u] = true;
        if(stack.contains(u)){
            // cycle detected
            return true;
        }
        stack.add(u);
        for(Integer v: adj.get(u)){
            if(dfs(v, adj, visited, stack)){
             return true;   
            }
        }
        stack.remove(u);
        return false;
    }
```  
  


  

### Components
- Every BFS/DFS runs on only a connected component within the graph
- To find all components in a graph, count the number of times we ran DFS on the input graph, as input graph can be made up of disjoint components
