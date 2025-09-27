#  Find the Single Number (Easy)


## Problem Statement : Given a non-empty array of integers where every element appears twice except one, find that single number.


## [LeetCode Problem](https://leetcode.com/problems/single-number/description/)

## Example :
- Input : arr=[2,4,3,5,5,4,2]
- Output : 3


### Brute Force Approach: 

**Step-by-step explanation:**
1. For each element, count how many times it appears using a loop.
2. If count is 1, return that element.


#### Java

```java

public int singleNumber(int[] nums) {
    for (int i = 0; i < nums.length; i++) {
        int count = 0;
        for (int j = 0; j < nums.length; j++)
            if (nums[j] == nums[i]) count++;
        if (count == 1) return nums[i];
    }
    return -1;
}
```

#### c++

```cpp

int singleNumber(vector<int>& nums) {
    for (int i = 0; i < nums.size(); i++) {
        int count = 0;
        for (int j = 0; j < nums.size(); j++)
            if (nums[j] == nums[i]) count++;
        if (count == 1) return nums[i];
    }
    return -1;
}
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. XOR all the numbers together – paired numbers cancel out.
2. The result is the single number.


#### java

``` java

public int singleNumber(int[] nums) {
    int result = 0;
    for (int num : nums) result ^= num;
    return result;
}
```

#### c++

``` cpp

int singleNumber(vector<int>& nums) {
    int result = 0;
    for (int num : nums) result ^= num;
    return result;
}   
```