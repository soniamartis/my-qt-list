# Graphs

### BFS Pattern
- Best for finding nodes closest from root
- Goes level by level

### DFS Pattern
- Goes path by path, where path = path from root to leaf

### Components
- Every BFS/DFS runs on only a connected component within the graph
- To find all components in a graph, count the number of times we ran DFS on the input graph, as input graph can be made up of disjoint components
