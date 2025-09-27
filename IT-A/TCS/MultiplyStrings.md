# Multiply Strings

### Problem : [Multiply Strings - Leetcode](https://leetcode.com/problems/multiply-strings/description/?envType=problem-list-v2&envId=string)

## Problem Statement

Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.

Note: You must not use any built-in BigInteger library or convert the inputs to integer directly.

**Constraints:**

1. 1 <= num1.length, num2.length <= 200
2. num1 and num2 consist of digits only.
3. Both num1 and num2 do not contain any leading zero, except the number 0 itself.

**Example 1:**
**Input:**
num1 = "2", num2 = "3"
**Output:**
"6"

#### Java

```java
class Solution {
    public String multiply(String num1, String num2) {
        if(num1.equals("0") || num2.equals("0")){
            return "0";
        }


        int arr[] = new int [num1.length() + num2.length()];
        for (int i=num1.length()-1;i>=0;i--){
            for(int j=num2.length()-1;j>=0;j--){
                int res = (num1.charAt(i)-'0')*(num2.charAt(j)-'0') + arr[i+j+1];
                arr[i+j+1]=res%10;
                arr[i+j] += res/10;
            }
        }

        StringBuilder sb = new StringBuilder();

        for(int k : arr){
            if(sb.length()==0 && k==0){
                continue;
            }
            sb.append(k);
        }
        return sb.toString();

    }
}
```

#### C++

```cpp
class Solution {
public:
    string multiply(string num1, string num2) {
        if (num1 == "0" || num2 == "0") return "0";

        vector<int> res(num1.size()+num2.size(), 0);

        for (int i = num1.size()-1; i >= 0; i--) {
            for (int j = num2.size()-1; j >= 0; j--) {
                res[i + j + 1] += (num1[i]-'0') * (num2[j]-'0');
                res[i + j] += res[i + j + 1] / 10;
                res[i + j + 1] %= 10;
            }
        }

        int i = 0;
        string ans = "";
        while (res[i] == 0) i++;
        while (i < res.size()) ans += to_string(res[i++]);

        return ans;
    }
};
```
