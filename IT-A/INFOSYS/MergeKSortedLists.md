## Problem Statement:  
You are given an array of `k` linked-lists, each linked-list is sorted in ascending order. Merge all the linked-lists into one sorted linked-list and return it.  

## [LeetCode Problem](https://leetcode.com/problems/merge-k-sorted-lists/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Collect all nodes’ values into a list.  
2. Sort the list.  
3. Build a new linked list.  

#### Java  

```java
public ListNode mergeKLists(ListNode[] lists) {
    List<Integer> vals = new ArrayList<>();
    for (ListNode l : lists) {
        while (l != null) {
            vals.add(l.val);
            l = l.next;
        }
    }
    Collections.sort(vals);
    ListNode dummy = new ListNode(0), curr = dummy;
    for (int v : vals) {
        curr.next = new ListNode(v);
        curr = curr.next;
    }
    return dummy.next;
}
```
C++
```cpp
ListNode* mergeKLists(vector<ListNode*>& lists) {
    vector<int> vals;
    for (auto l : lists) {
        while (l) {
            vals.push_back(l->val);
            l = l->next;
        }
    }
    sort(vals.begin(), vals.end());
    ListNode dummy(0), *curr = &dummy;
    for (int v : vals) {
        curr->next = new ListNode(v);
        curr = curr->next;
    }
    return dummy.next;
}
```
Optimal Approach:

Use a min-heap (priority queue) to always extract the smallest node. Complexity: O(N log k).
