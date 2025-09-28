#  Maximal Rectangle (Hard)


## Problem Statement : Given a binary matrix, find largest rectangle containing only 1’s.


## [LeetCode Problem](https://leetcode.com/problems/maximal-rectangle/description/)

## Example :
- Input : matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
- Output : 6
- Explaination : The maximal rectangle is shown in the above picture.


### Brute Force Approach: 

**Step-by-step explanation:**
1. For every cell, check all possible rectangles starting at this cell by growing width and height.


#### Java

```java

public int maximalRectangle(char[][] matrix) {
    int maxArea = 0, m = matrix.length, n = matrix[0].length;
    for (int i = 0; i < m; i++)
        for (int j = 0; j < n; j++)
            for (int k = i; k < m; k++)
                for (int l = j; l < n; l++) {
                    boolean isRect = true;
                    for (int x = i; x <= k; x++)
                        for (int y = j; y <= l; y++)
                            if (matrix[x][y] != '1') isRect = false;
                    if (isRect) maxArea = Math.max(maxArea, (k-i+1)*(l-j+1));
                }
    return maxArea;
}
```

#### c++

```cpp

int maximalRectangle(vector<vector<char>>& matrix) {
    int maxArea = 0, m = matrix.size(), n = matrix[0].size();
    for (int i = 0; i < m; i++)
        for (int j = 0; j < n; j++)
            for (int k = i; k < m; k++)
                for (int l = j; l < n; l++) {
                    bool isRect = true;
                    for (int x = i; x <= k; x++)
                        for (int y = j; y <= l; y++)
                            if (matrix[x][y] != '1') isRect = false;
                    if (isRect) maxArea = max(maxArea, (k-i+1)*(l-j+1));
                }
    return maxArea;
}
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. Treat each row as histogram; for each row compute largest rectangle.
2. Use largestRectangleArea for each row’s heights.


#### java

``` java

public int maximalRectangle(char[][] matrix) {
    if (matrix.length == 0) return 0;
    int maxArea = 0;
    int[] heights = new int[matrix[0].length];
    for (char[] row : matrix) {
        for (int i = 0; i < row.length; i++)
            heights[i] = row[i] == '1' ? heights[i]+1 : 0;
        maxArea = Math.max(maxArea, largestRectangleArea(heights));
    }
    return maxArea;
}
public int largestRectangleArea(int[] heights) {
    Stack<Integer> stack = new Stack<>();
    int maxArea = 0, n = heights.length;
    for (int i = 0; i <= n; i++) {
        int h = (i == n) ? 0 : heights[i];
        while (!stack.isEmpty() && h < heights[stack.peek()]) {
            int height = heights[stack.pop()];
            int width = stack.isEmpty() ? i : i - stack.peek() - 1;
            maxArea = Math.max(maxArea, height * width);
        }
        stack.push(i);
    }
    return maxArea;
}
```

#### c++

``` cpp

int largestRectangleArea(vector<int>& heights) {
    stack<int> s;
    int maxArea = 0, n = heights.size();
    for (int i = 0; i <= n; i++) {
        int h = (i == n) ? 0 : heights[i];
        while (!s.empty() && h < heights[s.top()]) {
            int height = heights[s.top()]; s.pop();
            int width = s.empty() ? i : i - s.top() - 1;
            maxArea = max(maxArea, height * width);
        }
        s.push(i);
    }
    return maxArea;
}
int maximalRectangle(vector<vector<char>>& matrix) {
    if(matrix.size()==0) return 0;
    int maxArea = 0, n = matrix[0].size();
    vector<int> heights(n,0);
    for(auto& row : matrix) {
        for(int i=0; i<n; i++)
            heights[i] = row[i]=='1' ? heights[i]+1 : 0;
        maxArea = max(maxArea, largestRectangleArea(heights));
    }
    return maxArea;
}  
```