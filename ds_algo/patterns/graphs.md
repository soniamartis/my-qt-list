# Graphs

## Notes
- In both graph traversals BFS and DFS, we need to maintain visited array to make sure we are not visiting the same node twice, esp. for undirected graphs

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


  

### Components
- Every BFS/DFS runs on only a connected component within the graph
- To find all components in a graph, count the number of times we ran DFS on the input graph, as input graph can be made up of disjoint components
