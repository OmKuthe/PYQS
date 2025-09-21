#  Add Two Numbers (Medium)


## Problem Statement: Given two non-empty linked lists representing two non-negative integers, add the two numbers and return the sum as a linked list. Each node contains a single digit and the digits are stored in reverse order.

## [LeetCode Problem](https://leetcode.com/problems/add-two-numbers/description/)

### Brute Force Approach: 

**Step-by-step explanation:**
1. Traverse both lists node by node.
2. Add each corresponding digit and track carry if the sum is ≥ 10.
3. Create nodes for each digit in the result list.
4. If carry remains after the last node, add a new node for carry.

#### Java

```java

public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(0), curr = dummy;
    int carry = 0;
    while (l1 != null || l2 != null) {
        int sum = carry;
        if (l1 != null) { 
            sum += l1.val; l1 = l1.next; }
        if (l2 != null) { 
            sum += l2.val; l2 = l2.next; }
        carry = sum / 10;
        curr.next = new ListNode(sum % 10);
        curr = curr.next;
    }
    if (carry > 0) curr.next = new ListNode(carry);
    return dummy.next;
}
```

#### c++

```cpp

ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    ListNode dummy(0), *curr = &dummy;
    int carry = 0;
    while (l1 || l2) {
        int sum = carry;
        if (l1) { sum += l1->val; l1 = l1->next; }
        if (l2) { sum += l2->val; l2 = l2->next; }
        carry = sum / 10;
        curr->next = new ListNode(sum % 10);
        curr = curr->next;
    }
    if (carry) curr->next = new ListNode(carry);
    return dummy.next;
}
```

## Optimal Approach: This brute force approach is already optimal (O(max(n,m))) since it's a simple pass with constant extra space.
