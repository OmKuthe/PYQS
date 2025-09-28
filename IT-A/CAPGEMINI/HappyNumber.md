#  Happy Number (Easy)


## Problem Statement : Write an algorithm to determine if a number n is a "happy" number. A number is happy if the sum of squares of its digits (done repeatedly) ends at 1.


## [LeetCode Problem](https://leetcode.com/problems/happy-number/description/)

## Example :
- Input : n = 19
- Output : true
- Explaination :
      - 12 + 92 = 82
      - 82 + 22 = 68
      - 62 + 82 = 100
      - 12 + 02 + 02 = 1


### Brute Force Approach: 

**Step-by-step explanation:**
1. Keep a set of seen numbers.
2. While n not 1 and n not seen before:
   - Add n to set.
   - Compute sum of squares of digits.
   - Replace n.
2. Return true if n is 1.


#### Java

```java

public boolean isHappy(int n) {
    Set<Integer> seen = new HashSet<>();
    while (n != 1 && !seen.contains(n)) {
        seen.add(n);
        int sum = 0;
        while (n > 0) {
            int d = n % 10;
            sum += d * d;
            n /= 10;
        }
        n = sum;
    }
    return n == 1;
}
```

#### c++

```cpp

bool isHappy(int n) {
    set<int> seen;
    while (n != 1 && !seen.count(n)) {
        seen.insert(n);
        int sum = 0, temp = n;
        while (temp > 0) {
            int d = temp % 10;
            sum += d * d;
            temp /= 10;
        }
        n = sum;
    }
    return n == 1;
}
```

### Optimal Approach: 

**Step-by-step Explanation:**
1. Use Floyd's cycle detection: fast/slow pointers on sequence.


#### java

``` java

int getNext(int n) {
    int sum = 0;
    while (n > 0) {
        int d = n % 10;
        sum += d * d;
        n /= 10;
    }
    return sum;
}
public boolean isHappy(int n) {
    int slow = n, fast = getNext(n);
    while (fast != 1 && slow != fast) {
        slow = getNext(slow);
        fast = getNext(getNext(fast));
    }
    return fast == 1;
}
```

#### c++

``` cpp

int getNext(int n) {
    int sum = 0;
    while (n > 0) {
        int d = n % 10;
        sum += d * d;
        n /= 10;
    }
    return sum;
}
bool isHappy(int n) {
    int slow = n, fast = getNext(n);
    while (fast != 1 && slow != fast) {
        slow = getNext(slow);
        fast = getNext(getNext(fast));
    }
    return fast == 1;
}   
```