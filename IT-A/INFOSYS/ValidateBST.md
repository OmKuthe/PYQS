## Problem Statement:  
Given the root of a binary tree, determine if it is a valid BST.  

## [LeetCode Problem](https://leetcode.com/problems/validate-binary-search-tree/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Perform inorder traversal.  
2. Store values in a list.  
3. Check if list is strictly increasing.  

#### Java  

```java
public boolean isValidBST(TreeNode root) {
    List<Integer> nums = new ArrayList<>();
    inorder(root, nums);
    for (int i = 1; i < nums.size(); i++) {
        if (nums.get(i) <= nums.get(i - 1)) return false;
    }
    return true;
}

private void inorder(TreeNode root, List<Integer> nums) {
    if (root == null) return;
    inorder(root.left, nums);
    nums.add(root.val);
    inorder(root.right, nums);
}
```
C++
```
class Solution {
public:
    void inorder(TreeNode* root, vector<int>& nums) {
        if (!root) return;
        inorder(root->left, nums);
        nums.push_back(root->val);
        inorder(root->right, nums);
    }
    
    bool isValidBST(TreeNode* root) {
        vector<int> nums;
        inorder(root, nums);
        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] <= nums[i-1]) return false;
        }
        return true;
    }
};
```
Optimal Approach:

Check validity using recursion with min/max bounds. Runs in O(n) time.
