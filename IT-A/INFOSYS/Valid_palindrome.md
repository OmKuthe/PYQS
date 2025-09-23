# Valid Palindrome (Easy)

## Problem Statement:  
Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.  
A string is a palindrome when it reads the same forward and backward, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters.  

## [LeetCode Problem](https://leetcode.com/problems/valid-palindrome/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Convert the string to lowercase.  
2. Remove all non-alphanumeric characters.  
3. Use two pointers: one at the beginning and one at the end.  
4. Compare characters; if they mismatch, return false.  
5. If all match, return true.  

#### Java  

```java
public boolean isPalindrome(String s) {
    s = s.toLowerCase().replaceAll("[^a-z0-9]", "");
    int left = 0, right = s.length() - 1;
    while (left < right) {
        if (s.charAt(left) != s.charAt(right)) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}
```

#### c++

```cpp
bool isPalindrome(string s) {
    string filtered = "";
    for (char c : s) {
        if (isalnum(c)) {
            filtered += tolower(c);
        }
    }
    int left = 0, right = filtered.size() - 1;
    while (left < right) {
        if (filtered[left] != filtered[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}
```
Optimal Approach:

The above solution is already optimal — it runs in O(n) time and uses O(1) extra space (ignoring the cleaned string).
