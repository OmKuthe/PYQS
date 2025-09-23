# Count Even and Odd Numbers (Easy)

## Problem Statement  
Given a non-empty linked list where each node contains a single digit, count the number of even and odd digits in the list and return them.

## [LeetCode Problem](https://leetcode.com/problems/count-good-numbers/)

### Brute Force Approach  

**Step-by-step explanation:**  
1. Traverse the linked list node by node.  
2. For each node, check if its value is even or odd.  
   - If even → increment even counter.  
   - If odd → increment odd counter.  
3. Continue until the end of the linked list.  
4. Return both counters as the result.  

#### Java

```java
public class Solution {
    public int[] countEvenOdd(ListNode head) {
        int evenCount = 0;
        int oddCount = 0;
        
        while (head != null) {
            if (head.val % 2 == 0) {
                evenCount++;
            } else {
                oddCount++;
            }
            head = head.next;
        }
        
        return new int[] {evenCount, oddCount};
    }
}
```
#### C++

```cpp
class Solution {
public:
    vector<int> countEvenOdd(ListNode* head) {
        int evenCount = 0;
        int oddCount = 0;
        
        while (head != nullptr) {
            if (head->val % 2 == 0) {
                evenCount++;
            } else {
                oddCount++;
            }
            head = head->next;
        }
        
        return {evenCount, oddCount};
    }
};
```
## Optimal Approach: This brute force approach is already optimal (O(n) time, O(1) space), since it only requires one traversal of the linked list.
