# Merge Two Sorted Lists (Easy)


## [LeetCode Problem](https://leetcode.com/problems/merge-two-sorted-lists/)

### Brute Force Approach: Append all nodes to a new list and sort.

**Step-by-step explanation:**
1. Traverse lists and collect values.
2. Sort the final collection.
3. Rebuild linked list.

#### Java

```java

public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    List<Integer> vals = new ArrayList<>();
    while (l1 != null) {
        vals.add(l1.val);
        l1 = l1.next;
    }
    while (l2 != null) {
        vals.add(l2.val);
        l2 = l2.next;
    }
    Collections.sort(vals);
    ListNode temp = new ListNode(0);
    ListNode curr = temp;
    for (int v : vals) {
        curr.next = new ListNode(v);
        curr = curr.next;
    }
    return temp.next;
}
```

#### c++

```cpp

ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    vector<int> vals;
    while (l1) {
        vals.push_back(l1->val);
        l1 = l1->next;
    }
    while (l2) {
        vals.push_back(l2->val);
        l2 = l2->next;
    }
    sort(vals.begin(), vals.end());
    ListNode temp(0);
    ListNode* curr = &temp;
    for (int v : vals) {
        curr->next = new ListNode(v);
        curr = curr->next;
    }
    return temp.next;
}
```

## Optimal Approach: Use a dummy node and a current pointer to build the merged list by comparing node values and attaching nodes iteratively.

**Step-by-step Explanation:**
1. Create a dummy node and a current pointer.
2. While both lists are non-empty, compare their front node values:
   - Attach the smaller node to the merged list.
   - Move forward in the list from which the node was taken.
3. If one list is exhausted, connect the rest of the other list.
4. Return the head of the merged list (`dummy.next`).


#### java

``` java

public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(0);
    ListNode current = dummy;
    while (l1 != null && l2 != null) {
        if (l1.val < l2.val) {
            current.next = l1;
            l1 = l1.next;
        } else {
            current.next = l2;
            l2 = l2.next;
        }
        current = current.next;
    }
    current.next = (l1 != null) ? l1 : l2;
    return dummy.next;
}
```

#### c++

``` cpp

ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    ListNode dummy(0);
    ListNode* current = &d ummy;
    while (l1 && l2) {
        if (l1->val < l2->val) {
            current->next = l1;
            l1 = l1->next;
        } else {
            current->next = l2;
            l2 = l2->next;
        }
        current = current->next;
    }
    current->next = l1 ? l1 : l2;
    return dummy.next;
}
```