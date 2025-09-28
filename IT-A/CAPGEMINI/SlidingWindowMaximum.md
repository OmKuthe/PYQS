#  Sliding Window Maximum (Hard)


## Problem Statement : Given an array and integer k, find the maximum in each sliding window of size k.


## [LeetCode Problem](https://leetcode.com/problems/sliding-window-maximum/description/)

## Example :
- Input : nums = [1,3,-1,-3,5,3,6,7], k = 3
- Output : [3,3,5,5,6,7]
- Explaination : 
``` 
Window position                Max
-----------------             -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
 ```


### Brute Force Approach: 

**Step-by-step explanation:**
1. For each window of k elements, scan all elements for max.
2. Add max to result.


#### Java

```java

public int[] maxSlidingWindow(int[] nums, int k) {
    int n=nums.length,[]res=new int[n-k+1];
    for(int i=0;i<=n-k;i++){
        int max=nums[i];
        for(int j=1;j<k;j++)
            if(nums[i+j]>max) max=nums[i+j];
        res[i]=max;
    }
    return res;
}
    return -1;
```

#### c++

```cpp

vector<int> maxSlidingWindow(vector<int>& nums, int k) {
    vector<int> res;
    for(int i=0;i<=nums.size()-k;i++){
        int maxVal=nums[i];
        for(int j=i;j<i+k;j++)
            maxVal=max(maxVal,nums[j]);
        res.push_back(maxVal);
    }
    return res;
}
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. Use a deque to keep indices of useful elements in decreasing order.
2. For each new element, remove indices out of window or smaller than current.


#### java

``` java

public int[] maxSlidingWindow(int[] nums, int k) {
    int n = nums.length;
    int[] res = new int[n - k + 1];
    Deque<Integer> dq = new LinkedList<>();
    for (int i = 0; i < n; i++) {
        while (!dq.isEmpty() && dq.peekFirst() < i - k + 1) dq.pollFirst();
        while (!dq.isEmpty() && nums[dq.peekLast()] < nums[i]) dq.pollLast();
        dq.offerLast(i);
        if (i >= k - 1) res[i - k + 1] = nums[dq.peekFirst()];
    }
    return res;
}
```

#### c++

``` cpp

vector<int> maxSlidingWindow(vector<int>& nums, int k) {
    deque<int> dq;
    vector<int> res;
    for (int i = 0; i < nums.size(); i++) {
        while (!dq.empty() && dq.front() < i - k + 1) dq.pop_front();
        while (!dq.empty() && nums[dq.back()] < nums[i]) dq.pop_back();
        dq.push_back(i);
        if (i >= k - 1) res.push_back(nums[dq.front()]);
    }
    return res;
} 
```