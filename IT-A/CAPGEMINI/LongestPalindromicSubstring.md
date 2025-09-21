# Longest Palindromic Substring (Medium)


## Problem Statement: Return the longest palindromic substring in a string.

## [LeetCode Problem](https://leetcode.com/problems/longest-palindromic-substring/description/)

### Brute Force Approach: 

**Step-by-step explanation:**
1. Check all possible substrings.
2. For each, check if palindrome.
3. Track longest palindrome substring.


#### Java

```java

public String longestPalindrome(String s) {
    String res = "";
    for (int i = 0; i < s.length(); i++)
        for (int j = i; j < s.length(); j++) {
            String sub = s.substring(i, j + 1);
            if (isPalindrome(sub) && sub.length() > res.length()) res = sub;
        }
    return res;
}
private boolean isPalindrome(String s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        if (s.charAt(left) != s.charAt(right)) return false;
        left++;
        right--;
    }
    return true;
}
```

#### c++

```cpp

string longestPalindrome(string s) {
    string res = "";
    for (int i = 0; i < s.size(); i++)
        for (int j = i + 1; j <= s.size(); j++) {
            string sub = s.substr(i, j-i);
            if (isPal(sub) && sub.size() > res.size()) res = sub;
        }
    return res;
}
bool isPal(string s) {
    int l=0, r=s.size()-1;
    while(l<r) if(s[l++]!=s[r--]) return false;
    return true;
}
```

## Optimal Approach: 

**Step-by-step Explanation:**
1. For each position, expand around center for odd & even length palindrome.
2. Track longest substring.


#### java

``` java

public String longestPalindrome(String s) {
    if (s == null || s.length() < 1) return "";
    int start = 0, end = 0;
    for (int i = 0; i < s.length(); i++) {
        int len1 = expandAroundCenter(s, i, i);
        int len2 = expandAroundCenter(s, i, i + 1);
        int len = Math.max(len1, len2);
        if (len > end - start) {
            start = i - (len -1) / 2;
            end = i + len / 2;
        }
    }
    return s.substring(start, end + 1);
}
private int expandAroundCenter(String s, int left, int right) {
    while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
        left--;
        right++;
    }
    return right - left -1;
}
```

#### c++

``` cpp

int expandAroundCenter(string s, int left, int right) {
    while (left >= 0 && right < s.size() && s[left] == s[right]) {
        left--; right++;
    }
    return right - left - 1;
}
string longestPalindrome(string s) {
    if (s.empty()) return "";
    int start = 0, end = 0;
    for (int i = 0; i < s.size(); i++) {
        int len1 = expandAroundCenter(s, i, i);
        int len2 = expandAroundCenter(s, i, i + 1);
        int len = max(len1, len2);
        if (len > end - start) {
            start = i - (len - 1) / 2;
            end = i + len / 2;
        }
    }
    return s.substr(start, end - start +1);
}   
```