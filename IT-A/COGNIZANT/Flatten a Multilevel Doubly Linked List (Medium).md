# Flatten a Multilevel Doubly Linked List (Medium)

## Problem Statement  
You are given a doubly linked list where in addition to the usual `next` and `prev` pointers, some nodes have a `child` pointer which may point to another doubly linked list (which in turn can have its own children, and so on).  

Your task is to flatten the list so that all the nodes appear in a single-level, doubly linked list. After flattening:

- All `child` pointers should be set to `null`.
- The `prev` and `next` pointers should reflect the new order.
- The relative order among nodes (in DFS / depth-first manner) should be preserved.  

If `head` is `null`, return `null`.  

🔗 **Problem Link:** [Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list)

---

## Example  

**Input:**

**Output (flattened):**

---

## Approach  

We can treat this problem as **DFS traversal of a multilevel linked structure**.

1. Traverse the list normally using a pointer `temp`.  
2. If a node has a `child`:  
   - Save its `next` node (if any) onto a stack.  
   - Set `temp.next = temp.child`, fix the `prev` pointer, and nullify the `child`.  
   - Continue traversal into the child list.  
3. If we reach the end of a list (`temp.next == null`) and the stack is not empty, pop from the stack and connect it as the `next`.  
4. Continue until the entire structure is flattened.  

This ensures depth-first order and maintains all `prev`/`next` relationships.

---

## Java Solution (Iterative with Stack)

```java
// Definition for a Node.
class Node {
    public int val;
    public Node prev;
    public Node next;
    public Node child;
}

class Solution {
    public Node flatten(Node head) {
        Node temp = head;
        Stack<Node> stack = new Stack<>();

        while (temp != null) {
            if (temp.child != null) {
                if (temp.next != null) {
                    stack.push(temp.next);
                }
                temp.next = temp.child;
                temp.child.prev = temp;
                temp.child = null;
                temp = temp.next;
                continue;
            }
            if (temp.next == null && !stack.isEmpty()) {
                Node node = stack.pop();
                temp.next = node;
                node.prev = temp;
            }
            temp = temp.next;
        }
        return head;
    }
}




