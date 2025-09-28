#  Add Digits Repeatedly (Easy)


## Problem Statement : Given an integer num, repeatedly add all its digits until the result has only one digit, and return it.


## [LeetCode Problem](https://leetcode.com/problems/add-digits/description/)

## Example :
- Input : num = 38
- Output : 2
- Explaination : The process is
38 --> 3 + 8 --> 11
11 --> 1 + 1 --> 2 
Since 2 has only one digit, return it.


### Brute Force Approach: 

**Step-by-step explanation:**
1.While num has more than one digit:
   - Sum its digits.
   - Replace num with sum.
2. Return num.


#### Java

```java

public int addDigits(int num) {
    while (num >= 10) {
        int sum = 0;
        while (num > 0) {
            sum += num % 10;
            num /= 10;
        }
        num = sum;
    }
    return num;
}
```

#### c++

```cpp

int addDigits(int num) {
    while (num >= 10) {
        int sum = 0, n = num;
        while (n > 0) {
            sum += n % 10;
            n /= 10;
        }
        num = sum;
    }
    return num;
}
```

### Optimal Approach: 

**Step-by-step Explanation:**
1. Use digital root formula:
    - If num == 0 return 0; else return 1 + ((num-1) % 9).


#### java

``` java

public int addDigits(int num) {
    if (num == 0) return 0;
    return 1 + (num - 1) % 9;
}
```

#### c++

``` cpp

int addDigits(int num) {
    if (num == 0) return 0;
    return 1 + (num - 1) % 9;
}   
```