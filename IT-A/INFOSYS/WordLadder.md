## Problem Statement:  
Given two words `beginWord` and `endWord`, and a dictionary word list, return the length of the shortest transformation sequence from `beginWord` to `endWord`.  

## [LeetCode Problem](https://leetcode.com/problems/word-ladder/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Generate all possible transformations.  
2. Use BFS to find shortest path.  

#### Java  

```java
public int ladderLength(String beginWord, String endWord, List<String> wordList) {
    Set<String> dict = new HashSet<>(wordList);
    if (!dict.contains(endWord)) return 0;
    Queue<String> q = new LinkedList<>();
    q.add(beginWord);
    int steps = 1;
    while (!q.isEmpty()) {
        int size = q.size();
        for (int i = 0; i < size; i++) {
            String word = q.poll();
            if (word.equals(endWord)) return steps;
            char[] arr = word.toCharArray();
            for (int j = 0; j < arr.length; j++) {
                char orig = arr[j];
                for (char c = 'a'; c <= 'z'; c++) {
                    arr[j] = c;
                    String next = new String(arr);
                    if (dict.remove(next)) q.add(next);
                }
                arr[j] = orig;
            }
        }
        steps++;
    }
    return 0;
}
```
C++
```cpp
int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
    unordered_set<string> dict(wordList.begin(), wordList.end());
    if (!dict.count(endWord)) return 0;
    queue<string> q;
    q.push(beginWord);
    int steps = 1;
    while (!q.empty()) {
        int size = q.size();
        for (int i = 0; i < size; i++) {
            string word = q.front(); q.pop();
            if (word == endWord) return steps;
            for (int j = 0; j < word.size(); j++) {
                char orig = word[j];
                for (char c = 'a'; c <= 'z'; c++) {
                    word[j] = c;
                    if (dict.count(word)) {
                        dict.erase(word);
                        q.push(word);
                    }
                }
                word[j] = orig;
            }
        }
        steps++;
    }
    return 0;
}
```
Optimal Approach:

Standard BFS is already optimal. Time complexity is O(N × wordLength × 26).
