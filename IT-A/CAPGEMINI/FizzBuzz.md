#  FizzBuzz (Easy)


## Problem Statement : Write numbers from 1 to n, but multiples of 3 as "Fizz", 5 as "Buzz", 15 as "FizzBuzz".


## [LeetCode Problem](https://leetcode.com/problems/fizz-buzz/description/)

## Example :
- Input : n = 5
- Output : ["1","2","Fizz","4","Buzz"]


### Brute Force Approach: 

**Step-by-step explanation:**
1. Loop i from 1 to n.
2. Print "FizzBuzz" if divisible by both 3 and 5.
3. Else print "Fizz" if divisible by 3, "Buzz" if 5, else number.


#### Java

```java

public List<String> fizzBuzz(int n) {
    List<String> res = new ArrayList<>();
    for (int i = 1; i <= n; i++) {
        if (i % 15 == 0) res.add("FizzBuzz");
        else if (i % 3 == 0) res.add("Fizz");
        else if (i % 5 == 0) res.add("Buzz");
        else res.add(String.valueOf(i));
    }
    return res;
}
```

#### c++

```cpp

vector<string> fizzBuzz(int n) {
    vector<string> res;
    for (int i = 1; i <= n; i++) {
        if (i % 15 == 0) res.push_back("FizzBuzz");
        else if (i % 3 == 0) res.push_back("Fizz");
        else if (i % 5 == 0) res.push_back("Buzz");
        else res.push_back(to_string(i));
    }
    return res;
}
```
