## Problem Statement:  
Given `n` non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.  

## [LeetCode Problem](https://leetcode.com/problems/trapping-rain-water/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. For each bar, find the highest bar on its left and right.  
2. Water trapped at that bar = `min(maxLeft, maxRight) - height[i]`.  
3. Sum over all bars.  

#### Java  

```java
public int trap(int[] height) {
    int n = height.length;
    int res = 0;
    for (int i = 0; i < n; i++) {
        int leftMax = 0, rightMax = 0;
        for (int j = i; j >= 0; j--) {
            leftMax = Math.max(leftMax, height[j]);
        }
        for (int j = i; j < n; j++) {
            rightMax = Math.max(rightMax, height[j]);
        }
        res += Math.min(leftMax, rightMax) - height[i];
    }
    return res;
}
```
C++
```cpp
int trap(vector<int>& height) {
    int n = height.size();
    int res = 0;
    for (int i = 0; i < n; i++) {
        int leftMax = 0, rightMax = 0;
        for (int j = i; j >= 0; j--) {
            leftMax = max(leftMax, height[j]);
        }
        for (int j = i; j < n; j++) {
            rightMax = max(rightMax, height[j]);
        }
        res += min(leftMax, rightMax) - height[i];
    }
    return res;
}
```
Optimal Approach:
Use two-pointer technique:
Keep track of leftMax and rightMax.
Move pointers inward depending on which side is smaller.
Accumulate trapped water.
This runs in O(n) time and O(1) space.
