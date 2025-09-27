#  3Sum (Medium)


## Problem Statement : Given array, find all triplets [a, b, c] that sum to zero.


## [LeetCode Problem](https://leetcode.com/problems/3sum/description/)

## Example :
- Input : nums = [-1,0,1,2,-1,-4]
- Output : [[-1,-1,2],[-1,0,1]]
- Explaination : nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
- Notice that the order of the output and the order of the triplets does not matter.

### Brute Force Approach: 

**Step-by-step explanation:**
1. Try every triplet
2. Add to list if sum is zero and triplet not already in list.


#### Java

```java

public List<List<Integer>> threeSum(int[] nums) {
    List<List<Integer>> res = new ArrayList<>();
    for (int i = 0; i < nums.length; i++)
        for (int j = i + 1; j < nums.length; j++)
            for (int k = j + 1; k < nums.length; k++)
                if (nums[i] + nums[j] + nums[k] == 0) {
                    List<Integer> triplet = Arrays.asList(nums[i], nums[j], nums[k]);
                    Collections.sort(triplet);
                    if (!res.contains(triplet))
                        res.add(triplet);
                }
    return res;
}
```

#### c++

```cpp

vector<vector<int>> threeSum(vector<int>& nums) {
    vector<vector<int>> res;
    int n = nums.size();
    for (int i = 0; i < n; i++)
        for (int j = i + 1; j < n; j++)
            for (int k = j + 1; k < n; k++)
                if (nums[i] + nums[j] + nums[k] == 0) {
                    vector<int> triplet = {nums[i], nums[j], nums[k]};
                    sort(triplet.begin(), triplet.end());
                    if (find(res.begin(), res.end(), triplet) == res.end())
                        res.push_back(triplet);
                }
    return res;
}
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. Sort the array.
2. For each value, use two pointers to find rest of the triplet.


#### java

``` java

public List<List<Integer>> threeSum(int[] nums) {
    Arrays.sort(nums);
    List<List<Integer>> res = new ArrayList<>();
    for (int i = 0; i < nums.length - 2; i++) {
        if (i > 0 && nums[i] == nums[i-1]) continue;
        int left = i + 1, right = nums.length - 1;
        while (left < right) {
            int sum = nums[i] + nums[left] + nums[right];
            if (sum == 0) {
                res.add(Arrays.asList(nums[i], nums[left++], nums[right--]));
                while (left < right && nums[left] == nums[left-1]) left++;
                while (left < right && nums[right] == nums[right+1]) right--;
            } else if (sum < 0) left++;
            else right--;
        }
    }
    return res;
}
```

#### c++

``` cpp

vector<vector<int>> threeSum(vector<int>& nums) {
    sort(nums.begin(), nums.end());
    vector<vector<int>> res;
    for (int i = 0; i < nums.size(); i++) {
        if (i > 0 && nums[i] == nums[i-1]) continue;
        int left = i+1, right = nums.size()-1;
        while (left < right) {
            int sum = nums[i] + nums[left] + nums[right];
            if (sum == 0) {
                res.push_back({nums[i], nums[left++], nums[right--]});
                while (left < right && nums[left] == nums[left-1]) left++;
                while (left < right && nums[right] == nums[right+1]) right--;
            } else if (sum < 0) left++;
            else right--;
        }
    }
    return res;
} 
```