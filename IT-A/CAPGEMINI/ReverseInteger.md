# Reverse Integer (Medium)


## Problem Statement: Reverse integer digits and return reversed number, 0 if overflow.

## [LeetCode Problem](https://leetcode.com/problems/reverse-integer/description/)

### Brute Force Approach: 

**Step-by-step explanation:**
1. Convert number to string.
2. Reverse it.
3. Parse to int; catch overflow.


#### Java

```java

public int reverse(int x) {
    try {
        String s = new StringBuilder(String.valueOf(Math.abs(x))).reverse().toString();
        int res = Integer.parseInt(s);
        return x < 0 ? -res : res;
    } catch (Exception e) {
        return 0;
    }
}
```

#### c++

```cpp

int reverse(int x) {
    string s = to_string(abs(x));
    reverse(s.begin(), s.end());
    try {
        long res = stol(s);
        if (res > INT_MAX) return 0;
        return x < 0 ? -res : res;
    } catch (...) {
        return 0;
    }
}
```

## Optimal Approach: 

**Step-by-step Explanation:**
1. Pop digit from end and push onto result.
2. Before pushing, check for overflow.


#### java

``` java

public int reverse(int x) {
    int rev = 0;
    while (x != 0) {
        int pop = x % 10;
        x /= 10;
        if (rev > Integer.MAX_VALUE/10 || rev < Integer.MIN_VALUE/10) return 0;
        rev = rev * 10 + pop;
    }
    return rev;
}
```

#### c++

``` cpp

int reverse(int x) {
    int rev = 0;
    while (x != 0) {
        int pop = x % 10;
        x /= 10;
        if (rev > INT_MAX/10 || rev < INT_MIN/10) return 0;
        rev = rev * 10 + pop;
    }
    return rev;
}   
```