# Kth Smallest Element in a BST (Medium)

## Problem Statement:  
Given the root of a binary search tree, and an integer `k`, return the `k`th smallest value (1-indexed) of all the values of the nodes in the tree.  

## [LeetCode Problem](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/)

### Brute Force Approach:  

**Step-by-step explanation:**  
1. Perform an inorder traversal of the BST (gives sorted values).  
2. Store values in a list.  
3. Return the element at index `k-1`.  

#### Java  

```java
public int kthSmallest(TreeNode root, int k) {
    List<Integer> nums = new ArrayList<>();
    inorder(root, nums);
    return nums.get(k - 1);
}

private void inorder(TreeNode root, List<Integer> nums) {
    if (root == null) return;
    inorder(root.left, nums);
    nums.add(root.val);
    inorder(root.right, nums);
}
```
####C++
```
class Solution {
public:
    void inorder(TreeNode* root, vector<int>& nums) {
        if (!root) return;
        inorder(root->left, nums);
        nums.push_back(root->val);
        inorder(root->right, nums);
    }
    
    int kthSmallest(TreeNode* root, int k) {
        vector<int> nums;
        inorder(root, nums);
        return nums[k - 1];
    }
};
```
Optimal Approach:

Use an inorder traversal with a counter, stopping once we reach the kth element. Runs in O(H + k) time (H = tree height).
