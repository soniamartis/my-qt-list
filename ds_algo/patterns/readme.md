# Patterns

## TODO : add templates for each pattern

## Linear Patterns
- used on linear data structures like arrays, linked lists adn strings

### 2 pointers O(N)
- Can either go in same direction or opposite direction
- Same direction: slow and fast pointer approach for detecting cycle in linked list or finding middle of the linkedlist in one pass
- Opposite direction: the array will be sorted mostly and are used for finding pairs

### Sliding window + HashMap O(N)
- Refined 2 pointer approach, where one pointer marks start of the window and other marks the end
- The size of the window can change dynamically
- Depending on the problem, either move the end pointer to expand the window, or move the start pointer to contract the window
- Longest subarra within array -> expand the window
- Shortest within the array -> contract the window
- Powerful pattern for tracking contiguous sequences
- It is used in conjunction with hashmaps to keep a track of the elements within the window

### Binary Search O(logN)
- Advanced 2 pointer as it uses left and right to find mid
- Used on sorted arrays, and works by dividing the array into halves till the criteria is met
- It can be used on any array that monotonically increases or decreases, and not only on array of numbers, even on array of True and False [F F F F T T]
- Another example is find minimum in rotated sorted array, again here, we can use a criteria to find mid, hence it qualifies as binsearch problem

## Non linear patterns
- Instead of treating trees and graphs as different structures, consider tree as a graph with no cycles
- Since graphs can have cycles, we need a visited set to keep track of nodes we already visited

### BFS
- Used to explore nodes in a graph/ tree by level
- Starts with the root and explores all its immediate neighbors first before going to the next neighbors's neighbors
- To make sure we do not revisit the nodes again, BFS uses a queue
- This queue contains nodes that are closest to the root and move outward
- Best for finding shortest path

### DFS
- While BFS goes level by level, DFS goes deep, fully exploring one path (root to leaf) before going to the next path
- In contrast to BFS, DFS uses a stack, its usually the call stack
- More suited for problems where u have to explore all paths 

### Backtracking
- DFS works on a prebuitl tree, whereeas in backtracking, we have to dynamically create the tree based on decisions made along the way
- When we hit a dead end and do not find the solution, we backtrack to the previoud decision and take another path

### Priority Queue
- 
