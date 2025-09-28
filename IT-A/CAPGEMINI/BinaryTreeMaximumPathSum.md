#  Binary Tree Maximum Path Sum (Hard)


## Problem Statement : Given a binary tree, find the path with maximum sum.


## [LeetCode Problem](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/)

## Example :
- Input : root = [1,2,3]
- Output : 6
- Explaination : The optimal path is 2 -> 1 -> 3 with a path sum of 2 + 1 + 3


### Brute Force Approach: 

**Step-by-step explanation:**
1. For each node, consider all possible paths through left/right recursively.
2. Track max seen.


- (Brute-force for trees is impractical; optimal provided.)


### Optimal Approach: 

**Step-by-step Explanation:**
1. Use recursion: For each node, compute max descending branch from left/right.
2. Max path at node = max of left branch, right branch, node val, left+node+right.
3. Track max across all nodes.


#### java

``` java

class Solution {
    int maxSum = Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {
        maxDown(root);
        return maxSum;
    }
    int maxDown(TreeNode node) {
        if (node == null) return 0;
        int left = Math.max(0, maxDown(node.left));
        int right = Math.max(0, maxDown(node.right));
        maxSum = Math.max(maxSum, left + node.val + right);
        return node.val + Math.max(left, right);
    }
}
```

#### c++

``` cpp

class Solution {
    int maxSum = INT_MIN;
    int maxDown(TreeNode* node) {
        if (!node) return 0;
        int left = max(0, maxDown(node->left));
        int right = max(0, maxDown(node->right));
        maxSum = max(maxSum, left + node->val + right);
        return node->val + max(left, right);
    }
public:
    int maxPathSum(TreeNode* root) {
        maxDown(root);
        return maxSum;
    }
};   
```