# Longest Common Subsequence (Medium)

## Problem Statement:  
Given two strings `text1` and `text2`, return the length of their longest common subsequence.  

## [LeetCode Problem](https://leetcode.com/problems/longest-common-subsequence/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Try all subsequences of `text1`.  
2. For each, check if it’s in `text2`.  
3. Track maximum length.  

#### Java  

```java
public int longestCommonSubsequence(String text1, String text2) {
    int m = text1.length(), n = text2.length();
    int[][] dp = new int[m+1][n+1];
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (text1.charAt(i-1) == text2.charAt(j-1))
                dp[i][j] = 1 + dp[i-1][j-1];
            else
                dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
        }
    }
    return dp[m][n];
}
```
C++
```cpp
int longestCommonSubsequence(string text1, string text2) {
    int m = text1.size(), n = text2.size();
    vector<vector<int>> dp(m+1, vector<int>(n+1, 0));
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (text1[i-1] == text2[j-1])
                dp[i][j] = 1 + dp[i-1][j-1];
            else
                dp[i][j] = max(dp[i-1][j], dp[i][j-1]);
        }
    }
    return dp[m][n];
}
```
Optimal Approach:

Dynamic Programming with O(m × n) time and space.
