**Problem Statement:**  
Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.  
A string is a palindrome if it reads the same forward and backward after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters.  

**LeetCode Problem:** [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

---

## Brute Force Approach:
1. Convert the string to lowercase.  
2. Remove all characters that are not letters or digits.  
3. Reverse the string and compare with the original cleaned string.  
4. If both are equal → palindrome, else not.  

---

## Java
```java
class Solution {
    public boolean isPalindrome(String s) {
        String cleaned = s.replaceAll("[^A-Za-z0-9]", "").toLowerCase();
        String reversed = new StringBuilder(cleaned).reverse().toString();
        return cleaned.equals(reversed);
    }
}

##C++
class Solution {
public:
    bool isPalindrome(string s) {
        string cleaned;
        for (char c : s) {
            if (isalnum(c)) cleaned += tolower(c);
        }
        string reversed = cleaned;
        reverse(reversed.begin(), reversed.end());
        return cleaned == reversed;
    }
};

Optimal Approach:

Use two pointers (left, right).

Move inward while skipping non-alphanumeric characters.

Compare characters in constant space.

Time Complexity: O(n)

Space Complexity: O(1)
