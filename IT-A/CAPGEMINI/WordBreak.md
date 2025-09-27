#  Word Break (Medium)


## Problem Statement : Given a string and a word dictionary, return if string can be segmented into space-separated words from dictionary.


## [LeetCode Problem](https://leetcode.com/problems/word-break/description/)

## Example 1:
- Input : s = "leetcode", wordDict = ["leet","code"]
- Output : true
- Explaination : Return true because "leetcode" can be segmented as "leet code".

## Example 2:
- Input : s = "catsandog", wordDict = ["cats","dog","sand","and","cat"]
- Output : false
- Explaination : Return false because "catsandog" can't be segmented as "cats and dog" as one 'd' char is not present.


### Brute Force Approach: 

**Step-by-step explanation:**
1. Try all partitions recursively; check if prefix in dictionary and suffix can be broken (slow for long strings).


#### Java

```java

public boolean wordBreak(String s, List<String> wordDict) {
    Set<String> dict = new HashSet<>(wordDict);
    return canBreak(s, dict);
}
private boolean canBreak(String s, Set<String> dict) {
    if (s.isEmpty()) return true;
    for (int i = 1; i <= s.length(); i++)
        if (dict.contains(s.substring(0, i)) && canBreak(s.substring(i), dict))
            return true;
    return false;
}
```

#### c++

```cpp

bool canBreak(string s, unordered_set<string>& dict) {
    if (s.empty()) return true;
    for (int i = 1; i <= s.size(); i++)
        if (dict.count(s.substr(0, i)) && canBreak(s.substr(i), dict))
            return true;
    return false;
}
bool wordBreak(string s, vector<string>& wordDict) {
    unordered_set<string> dict(wordDict.begin(), wordDict.end());
    return canBreak(s, dict);
}
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. Use DP: dp[i] true if s[0..i-1] can be segmented.
2. For each i, try all j < i and check if dp[j] true and s[j:i] in dictionary.


#### java

``` java

public boolean wordBreak(String s, List<String> wordDict) {
    Set<String> dict = new HashSet<>(wordDict);
    boolean[] dp = new boolean[s.length() + 1];
    dp[0] = true;
    for (int i = 1; i <= s.length(); i++)
        for (int j = 0; j < i; j++)
            if (dp[j] && dict.contains(s.substring(j, i))) {
                dp[i] = true;
                break;
            }
    return dp[s.length()];
}
```

#### c++

``` cpp

bool wordBreak(string s, vector<string>& wordDict) {
    unordered_set<string> dict(wordDict.begin(), wordDict.end());
    vector<bool> dp(s.size() + 1, false);
    dp[0] = true;
    for (int i = 1; i <= s.size(); i++)
        for (int j = 0; j < i; j++)
            if (dp[j] && dict.count(s.substr(j, i-j))) {
                dp[i] = true;
                break;
            }
    return dp[s.size()];
}  
```