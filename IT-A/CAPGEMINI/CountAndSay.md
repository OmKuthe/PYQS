#  Count and Say (Easy)


## Problem Statement : The count-and-say sequence is defined as: "1" is the first term. Each subsequent term describes the previous term. Return the nth term as a string.


## [LeetCode Problem](https://leetcode.com/problems/count-and-say/description/)

## Example :
- Input : n = 4
- Output : "1211"
- Explaination :
      - countAndSay(1) = "1"
      - countAndSay(2) = RLE of "1" = "11"
      - countAndSay(3) = RLE of "11" = "21"
      - countAndSay(4) = RLE of "21" = "1211"


### Brute Force Approach: 

**Step-by-step explanation:**
1. Start with "1".
2. For each iteration, count consecutive identical digits and build new string.
3. Repeat n-1 times.


#### Java

```java

public String countAndSay(int n) {
    String s = "1";
    for (int i = 1; i < n; i++) {
        StringBuilder sb = new StringBuilder();
        for (int j = 0; j < s.length(); ) {
            int k = j;
            while (k < s.length() && s.charAt(k) == s.charAt(j)) k++;
            sb.append(k - j).append(s.charAt(j));
            j = k;
        }
        s = sb.toString();
    }
    return s;
}
```

#### c++

```cpp

string countAndSay(int n) {
    string s = "1";
    for (int i = 1; i < n; i++) {
        string t = "";
        for (int j = 0; j < s.size(); ) {
            int k = j;
            while (k < s.size() && s[k] == s[j]) k++;
            t += to_string(k-j) + s[j];
            j = k;
        }
        s = t;
    }
    return s;
}
```

### Optimal Approach: 

- (Same as brute force, as each term must be generated iteratively.)


