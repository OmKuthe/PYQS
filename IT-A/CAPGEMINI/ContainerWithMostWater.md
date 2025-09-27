# Container With Most Water (Medium)


## Problem Statement : Find two lines in an array that trap the most water.

## [LeetCode Problem](https://leetcode.com/problems/container-with-most-water/description/)

### Brute Force Approach: 

**Step-by-step explanation:**
1. Try every pair and calculate water area.
2. Track max area.


#### Java

```java

public int maxArea(int[] height) {
    int max = 0;
    for (int i = 0; i < height.length; i++) {
        for (int j = i + 1; j < height.length; j++) {
            int area = Math.min(height[i], height[j]) * (j - i);
            if (area > max) max = area;
        }
    }
    return max;
}
```

#### c++

```cpp

int maxArea(vector<int>& height) {
    int maxArea = 0;
    for (int i = 0; i < height.size(); i++) {
        for (int j = i + 1; j < height.size(); j++) {
            int area = min(height[i], height[j]) * (j - i);
            maxArea = max(maxArea, area);
        }
    }
    return maxArea;
}
```

## Optimal Approach: 

**Step-by-step Explanation:**
1. Use two pointers at start and end.
2. Calculate area, update max.
3. Move pointer pointing to smaller height inward.
4. Repeat until pointers meet.


#### java

``` java

public int maxArea(int[] height) {
    int max = 0, left = 0, right = height.length - 1;
    while (left < right) {
        int area = Math.min(height[left], height[right]) * (right - left);
        if (area > max) max = area;
        if (height[left] < height[right]) left++;
        else right--;
    }
    return max;
}
```

#### c++

``` cpp

int maxArea(vector<int>& height) {
    int maxArea = 0, left = 0, right = height.size() - 1;
    while (left < right) {
        int area = min(height[left], height[right]) * (right - left);
        maxArea = max(maxArea, area);
        if (height[left] < height[right]) left++;
        else right--;
    }
    return maxArea;
}  
```