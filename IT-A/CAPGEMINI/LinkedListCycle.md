#  Linked List Cycle (Medium)


## Problem Statement : Given a linked list, determine if there is a cycle.


## [LeetCode Problem](https://leetcode.com/problems/linked-list-cycle/description/)

## Example :
- Input : head = [3,2,0,-4], pos = 1
- Output : true
- Explaination : There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
- 

### Brute Force Approach: 

**Step-by-step explanation:**
1. Use a list/set to keep visited nodes.
2. As you traverse, if a node is seen again, cycle exists.


#### Java

```java

public boolean hasCycle(ListNode head) {
    Set<ListNode> seen = new HashSet<>();
    while (head != null) {
        if (seen.contains(head)) return true;
        seen.add(head);
        head = head.next;
    }
    return false;
}
```

#### c++

```cpp

bool hasCycle(ListNode *head) {
    set<ListNode*> seen;
    while (head) {
        if (seen.count(head)) return true;
        seen.insert(head);
        head = head->next;
    }
    return false;
}
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. Use two pointers, slow and fast.
2. If they meet, there’s a cycle.


#### java

``` java

public boolean hasCycle(ListNode head) {
    if (head == null) return false;
    ListNode slow = head, fast = head.next;
    while (fast != null && fast.next != null) {
        if (slow == fast) return true;
        slow = slow.next;
        fast = fast.next.next;
    }
    return false;
}
```

#### c++

``` cpp

bool hasCycle(ListNode *head) {
    if (!head) return false;
    ListNode *slow = head, *fast = head->next;
    while (fast && fast->next) {
        if (slow == fast) return true;
        slow = slow->next;
        fast = fast->next->next;
    }
    return false;
}
```