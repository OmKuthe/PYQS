
# Search in Rotated Sorted Array (Medium)

## Problem Statement:  
Given the array `nums` sorted in ascending order, and rotated at some pivot unknown, search for a target value. If found, return its index, else return -1.  

## [LeetCode Problem](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Traverse the entire array.  
2. If element matches target, return index.  
3. Else return -1.

#### Java  

```java
public int search(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) return i;
    }
    return -1;
}
```
C++
```cpp
int search(vector<int>& nums, int target) {
    for (int i = 0; i < nums.size(); i++) {
        if (nums[i] == target) return i;
    }
    return -1;
}
```
Optimal Approach:

Binary search by checking which half is sorted. Runs in O(log n).

---
