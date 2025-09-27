#  Min Stack (Medium)


## Problem Statement : Design a stack that supports push, pop, top, and retrieving the minimum.


## [LeetCode Problem](https://leetcode.com/problems/min-stack/description/)

## Example :
- Input : ["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]
- Output : [null,null,null,null,-3,null,0,-2]
- Explaination :
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2 


### Brute Force Approach: 

**Step-by-step explanation:**
1. Use a list/stack for values.
2. To get min, traverse all values.


#### Java

```java

class MinStack {
    Stack<Integer> stack = new Stack<>();
    public void push(int val) { stack.push(val); }
    public void pop() { stack.pop(); }
    public int top() { return stack.peek(); }
    public int getMin() {
        int min = Integer.MAX_VALUE;
        for (int num : stack) min = Math.min(min, num);
        return min;
    }
}
```

#### c++

```cpp

class MinStack {
    stack<int> s;
public:
    void push(int val) { s.push(val); }
    void pop() { s.pop(); }
    int top() { return s.top(); }
    int getMin() {
        int m = INT_MAX;
        stack<int> temp = s;
        while (!temp.empty()) {
            m = min(m, temp.top());
            temp.pop();
        }
        return m;
    }
};
```


### Optimal Approach: 

**Step-by-step Explanation:**
1. Along with value stack, keep a min stack.

## Example : Push 2, 0, 3, 0;  GetMin→0, Pop; GetMin→0, Pop; GetMin→0, Pop; GetMin→2


#### java

``` java

class MinStack {
    Stack<Integer> stack = new Stack<>();
    Stack<Integer> minStack = new Stack<>();
    public void push(int val) {
        stack.push(val);
        if (minStack.isEmpty() || val <= minStack.peek())
            minStack.push(val);
    }
    public void pop() {
        if (stack.pop().equals(minStack.peek()))
            minStack.pop();
    }
    public int top() { return stack.peek(); }
    public int getMin() { return minStack.peek(); }
}
```

#### c++

``` cpp

class MinStack {
    stack<int> s, minS;
public:
    void push(int val) {
        s.push(val);
        if (minS.empty() || val <= minS.top()) minS.push(val);
    }
    void pop() {
        if (s.top() == minS.top()) minS.pop();
        s.pop();
    }
    int top() { return s.top(); }
    int getMin() { return minS.top(); }
};  
```