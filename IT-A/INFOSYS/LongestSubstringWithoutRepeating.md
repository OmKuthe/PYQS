# Longest Substring Without Repeating Characters (Medium)

## Problem Statement:  
Given a string `s`, find the length of the longest substring without repeating characters.  

## [LeetCode Problem](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Generate all substrings.  
2. Check if each substring has all unique characters.  
3. Track maximum length.  

#### Java  

```java
public int lengthOfLongestSubstring(String s) {
    int n = s.length(), maxLen = 0;
    for (int i = 0; i < n; i++) {
        Set<Character> set = new HashSet<>();
        for (int j = i; j < n; j++) {
            if (set.contains(s.charAt(j))) break;
            set.add(s.charAt(j));
            maxLen = Math.max(maxLen, j - i + 1);
        }
    }
    return maxLen;
}
```
C++
```cpp
int lengthOfLongestSubstring(string s) {
    int n = s.size(), maxLen = 0;
    for (int i = 0; i < n; i++) {
        unordered_set<char> set;
        for (int j = i; j < n; j++) {
            if (set.count(s[j])) break;
            set.insert(s[j]);
            maxLen = max(maxLen, j - i + 1);
        }
    }
    return maxLen;
}
```
Optimal Approach:

Sliding window + hashset for uniqueness. Runs in O(n) time.
