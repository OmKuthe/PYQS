# Median of Two Sorted Arrays (Hard)


## Problem Statement : Given two sorted arrays, nums1 and nums2, find the median of the two sorted arrays.

## [LeetCode Problem](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)

### Brute Force Approach: 

**Step-by-step explanation:**
1. Concatenate arrays and sort.
2. Find the median element(s) by index.

#### Java

```java

public double findMedianSortedArrays(int[] a, int[] b) {
    int[] m = new int[a.length + b.length];
    int i=0, j=0, k=0;
    while (i < a.length && j < b.length)
        m[k++] = a[i] < b[j] ? a[i++] : b[j++];
    while (i < a.length) 
        m[k++] = a[i++];
    while (j < b.length) 
        m[k++] = b[j++];
    int mid = m.length/2;
    return m.length%2==0 ? (m[mid-1]+m[mid])/2.0 : m[mid];
}
```

#### c++

```cpp

double findMedianSortedArrays(vector<int>& a, vector<int>& b) {
    vector<int> m;
    int i=0, j=0;
    while (i < a.size() && j < b.size())
        m.push_back(a[i] < b[j] ? a[i++] : b[j++]);
    while (i < a.size()) 
        m.push_back(a[i++]);
    while (j < b.size()) 
        m.push_back(b[j++]);
    int mid = m.size()/2;
    return m.size()%2==0 ? (m[mid-1]+m[mid])/2.0 : m[mid];
}
```

## Optimal Approach: Binary search solution is complex; interviewers accept the brute force merge for clarity in many cases.
