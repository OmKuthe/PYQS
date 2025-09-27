#  Move Zeros to End (Easy)


## Problem Statement : Move all zeros in array to end, maintain order of non-zeros.


## [LeetCode Problem](https://leetcode.com/problems/move-zeroes/description/)

## Example :
- Input : nums = [0,1,0,3,12]
- Output : [1,3,12,0,0]


### Brute Force Approach: 

**Step-by-step explanation:**
1. Create a new array/list.
2. First, add all non-zeros.
3. Then, add all zeros.


#### Java

```java

public int[] moveZeroes(int[] nums) {
    int[] res = new int[nums.length];
    int k = 0;
    for (int i = 0; i < nums.length; i++)
        if (nums[i] != 0) res[k++] = nums[i];
    for (int i = k; i < nums.length; i++)
        res[i] = 0;
    return res;
}
```

#### c++

```cpp

vector<int> moveZeroes(vector<int>& nums) {
    vector<int> res(nums.size(), 0);
    int k = 0;
    for (int i = 0; i < nums.size(); i++)
        if (nums[i] != 0) res[k++] = nums[i];
    return res;
}
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. Use two pointers (slow for next non-zero).
2. For each, if non-zero, place at slow and increment.
3. Fill rest with zeros.


#### java

``` java

public void moveZeroes(int[] nums) {
    int slow = 0;
    for (int i = 0; i < nums.length; i++)
        if (nums[i] != 0) nums[slow++] = nums[i];
    while (slow < nums.length)
        nums[slow++] = 0;
}
```

#### c++

``` cpp

void moveZeroes(vector<int>& nums) {
    int slow = 0;
    for (int i = 0; i < nums.size(); i++)
        if (nums[i] != 0) nums[slow++] = nums[i];
    while (slow < nums.size())
        nums[slow++] = 0;
}  
```