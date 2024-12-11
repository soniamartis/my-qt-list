# Patterns

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
- 
