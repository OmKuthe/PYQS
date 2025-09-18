# Rotate Array

## Brute Force Approach (Using Tempory Array)

### The Problems : [Roatate Array - LeetCode](https://leetcode.com/problems/rotate-array)

- Create a temporary array of size n
- Copy First X positions elements in temp
- Add Remaining N-X positions values in temp
- Copy temporary array to nums array

#### Java

```java
class Solution{
    public void RotateToRight(int nums[]  int k){
        int n = nums.length;

        k = k%n;
        int[] temp = new int[n];
        for(int i = 0; i < k; i++){
            temp[i] = nums[n-k + i];
        }
        for(int i = k; i < n; i++){
            temp[i] = nums[i-k];
        }
        for(int i= 0; i < n; i++){
            nums[i] = temp[i];
        }
    }
}
```

#### C++

```cpp

class Solution{
    public void RotateToRight(vector<int>&nums,  int k){
        int n = nums.size();

        vector<int> temp(n);

        k = k%n;

        for(int i = 0; i < k; i++){
            temp[i] = nums[n-k + i];
        }
        for(int i = k; i < n; i++){
            temp[i] = nums[i-k];
        }
        nums = temp;
    }
};
```

## Reversal Algorithm (Optimal)

In this approach ,

- We simply reverse X position element
- Reverse Remaming N-X position elements
- Reverse entire array

For Example : `int[] arr = [1, 2, 3, 4 ,5 ,6, 7] and  k = 3`

- After reverse idx 0 to idx 3 elements:
  `int[] arr = [3, 2, 1 , 4, 5 , 6, 7]`
- Then Reverse index 4 to idx 6 elements:
  `int[] arr = [3, 2, 1 , 7, 6, 5, 4]`
- Now, Reverse entire array:
  `int[] arr = [4, 5, 6, 7, 1, 2, 3]`

  ```java
    class Solution {

        void reverse(int[] nums, int start, int end){
            while(start < end){
                int temp = nums[start];
                nums[start] = nums[end];
                nums[end] = temp;

                start++;
                end--;
            }
        }
        void rotate(int[] nums, int k) {
            int n = nums.length;
            k = k % n;
            reverse(nums, 0, n -1 );
            reverse(nums, 0, k - 1);
            reverse(nums, k, n - 1);

        }
  }
  ```

  ```cpp
  class Solution {
  public:

    void reverse(vector<int>& nums, int start, int end){
        while(start < end){
            std::swap(nums[start], nums[end]);
            start++;
            end--;
        }
    }
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n;
        reverse(nums, 0, n -1 );
        reverse(nums, 0, k - 1);
        reverse(nums, k, n - 1);

    }
  };

  ```
