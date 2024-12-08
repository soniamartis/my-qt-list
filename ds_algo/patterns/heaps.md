# Heap Patterns

- To find the last node in heap array that has any children do (n/2) - 1
- A heapify function always moves downwards
- A decreaseKey/ incraesekey will always move upwards towards the parent

## How to identify its heap problem
- Kth largest/ smallest -> means a heap of K elements
- If u find urself creating a PQ of N elements instead of K, then might as well just sort the array, as its the same time complexity and better space complexity than a PQ



### Kth largest
- In a min-heap of K elements, the element at the root is the smallest in the grp of K elements


### Java methods
- Default Min heap
```java 
Queue<Integer> pq =  new PriorityQueue<>();
```
- Max heap
``` java
Queue<Integer> pq =  new PriorityQueue<>(Collections.reverseOrder());
```
 


