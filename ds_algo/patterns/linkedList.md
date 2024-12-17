# Linked List Patterns

## Middle of list
- Use slow and fast pointers
```java
int getMiddle(Node head) {
        // Your code here.
       Node slow = head, fast = head;
       while(fast != null && fast.next != null){
           fast = fast.next.next;
           slow = slow.next;
       }
       return slow.data;
    }
```
