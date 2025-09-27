#  Remove Duplicates From Sorted Array (Easy)


## Problem Statement : Remove duplicates in-place, return length of the unique array prefix.


## [LeetCode Problem](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

## Example :
- Input : nums = [0,0,1,1,1,2,2,3,3,4]
- Output : 5, nums = [0,1,2,3,4,_,_,_,_,_]
- Explaination : Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores). 


### Brute Force Approach: 

**Step-by-step explanation:**
1. Use a new array/list for unique elements.
2. Loop, add element if not already present.


#### Java

```java

public int removeDuplicates(int[] nums) {
    ArrayList<Integer> uniq = new ArrayList<>();
    for (int i = 0; i < nums.length; i++)
        if (!uniq.contains(nums[i])) uniq.add(nums[i]);
    for (int i = 0; i < uniq.size(); i++)
        nums[i] = uniq.get(i);
    return uniq.size();
}
```

#### c++

```cpp

int removeDuplicates(vector<int>& nums) {
    vector<int> uniq;
    for (int i = 0; i < nums.size(); i++) {
        bool found = false;
        for (int j = 0; j < uniq.size(); j++)
            if (uniq[j] == nums[i]) found = true;
        if (!found) uniq.push_back(nums[i]);
    }
    for (int i = 0; i < uniq.size(); i++)
        nums[i] = uniq[i];
    return uniq.size();
}
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. Use two pointers: first marks last unique.
2. If next element is different, move unique pointer and set value.


#### java

``` java

public int removeDuplicates(int[] nums) {
    if (nums.length == 0) return 0;
    int i = 0;
    for (int j = 1; j < nums.length; j++)
        if (nums[j] != nums[i]) nums[++i] = nums[j];
    return i + 1;
}
```

#### c++

``` cpp

int removeDuplicates(vector<int>& nums) {
    if (nums.size() == 0) return 0;
    int i = 0;
    for (int j = 1; j < nums.size(); j++)
        if (nums[j] != nums[i]) nums[++i] = nums[j];
    return i + 1;
} 
```