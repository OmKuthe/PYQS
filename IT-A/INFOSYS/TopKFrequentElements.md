## Problem Statement:  
Given an integer array `nums` and an integer `k`, return the `k` most frequent elements.  

## [LeetCode Problem](https://leetcode.com/problems/top-k-frequent-elements/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Count frequency of each number.  
2. Sort numbers by frequency.  
3. Take top `k`.  

#### Java  

```java
public int[] topKFrequent(int[] nums, int k) {
    Map<Integer, Integer> freq = new HashMap<>();
    for (int n : nums) freq.put(n, freq.getOrDefault(n, 0) + 1);
    List<Map.Entry<Integer, Integer>> list = new ArrayList<>(freq.entrySet());
    list.sort((a, b) -> b.getValue() - a.getValue());
    int[] res = new int[k];
    for (int i = 0; i < k; i++) res[i] = list.get(i).getKey();
    return res;
}
```
C++
```cpp
vector<int> topKFrequent(vector<int>& nums, int k) {
    unordered_map<int,int> freq;
    for (int n : nums) freq[n]++;
    vector<pair<int,int>> vec(freq.begin(), freq.end());
    sort(vec.begin(), vec.end(), [](auto &a, auto &b) {
        return b.second < a.second;
    });
    vector<int> res;
    for (int i = 0; i < k; i++) res.push_back(vec[i].first);
    return res;
}
```
Optimal Approach:

Use a min-heap of size k or bucket sort. Runs in O(n log k) or O(n).
