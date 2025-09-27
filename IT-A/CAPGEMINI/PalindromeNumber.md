# Reverse Integer (Medium)


## Problem Statement : Check if integer is palindrome.

## [LeetCode Problem](https://leetcode.com/problems/palindrome-number/description/)

### Brute Force Approach: 

**Step-by-step explanation:**
1. Convert number to string.
2. Check if string is equal to reverse.


#### Java

```java

public boolean isPalindrome(int x) {
    String s = String.valueOf(x);
    String r = new StringBuilder(s).reverse().toString();
    return s.equals(r);
}
```

#### c++

```cpp

bool isPalindrome(int x) {
    string s = to_string(x);
    string r = s;
    reverse(r.begin(), r.end());
    return s == r;
}
```

## Optimal Approach: 

**Step-by-step Explanation:**
1. If negative or ends with 0 (except 0), return false.
2. Reverse half the integer.
3. Compare halves.


#### java

``` java

public boolean isPalindrome(int x) {
    if (x < 0 || (x % 10 == 0 && x != 0)) return false;
    int rev = 0;
    while (x > rev) {
        rev = rev * 10 + x % 10;
        x /= 10;
    }
    return x == rev || x == rev / 10;
}
```

#### c++

``` cpp

bool isPalindrome(int x) {
    if (x < 0 || (x % 10 == 0 && x != 0)) return false;
    int rev = 0;
    while (x > rev) {
        rev = rev * 10 + x % 10;
        x /= 10;
    }
    return x == rev || x == rev / 10;
}   
```