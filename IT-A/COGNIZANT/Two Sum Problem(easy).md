### 🔹 Easy Level

1.  **Two Sum Problem**
    
    *   **Platform:** [LeetCode – Two Sum](https://leetcode.com/problems/two-sum/description/)
        
    *   **Problem:** Find indices of two numbers that add up to a target.
        
    *   **Approaches:**
        
        *   Brute Force → O(n²)
            
        *   HashMap → O(n) (optimal)

### Approach 1: Brute Force

**Algorithm**

The brute force approach is simple. Loop through each element _x_ and find if there is another value that equals to _target_−_x_.

**Implementation**

class Solution {

public int\[\] twoSum(int\[\] nums, int target) {

for (int i = 0; i < nums.length; i++) {

for (int j = i + 1; j < nums.length; j++) {

if (nums\[j\] == target - nums\[i\]) {

return new int\[\] { i, j };

}

}

}

// If no valid pair is found, return an empty array instead of null

return new int\[\] {};

}

}

**Complexity Analysis**

*   Time complexity: _O_(_n_2).For each element, we try to find its complement by looping through the rest of the array which takes _O_(_n_) time. Therefore, the time complexity is _O_(_n_2).
    
*   Space complexity: _O_(1).The space required does not depend on the size of the input array, so only constant space is used.
    

### Approach 2: Two-pass Hash Table

**Intuition**

To improve our runtime complexity, we need a more efficient way to check if the complement exists in the array. If the complement exists, we need to get its index. What is the best way to maintain a mapping of each element in the array to its index? A hash table.

We can reduce the lookup time from _O_(_n_) to _O_(1) by trading space for speed. A hash table is well suited for this purpose because it supports fast lookup in _near_ constant time. I say "near" because if a collision occurred, a lookup could degenerate to _O_(_n_) time. However, lookup in a hash table should be amortized _O_(1) time as long as the hash function was chosen carefully.

**Algorithm**

A simple implementation uses two iterations. In the first iteration, we add each element's value as a key and its index as a value to the hash table. Then, in the second iteration, we check if each element's complement (_target_−_nums_\[_i_\]) exists in the hash table. If it does exist, we return current element's index and its complement's index. Beware that the complement must not be _nums_\[_i_\] itself!

**Implementation**

class Solution {

public int\[\] twoSum(int\[\] nums, int target) {

Map map = new HashMap<>();

for (int i = 0; i < nums.length; i++) {

map.put(nums\[i\], i);

}

for (int i = 0; i < nums.length; i++) {

int complement = target - nums\[i\];

if (map.containsKey(complement) && map.get(complement) != i) {

return new int\[\] { i, map.get(complement) };

}

}

// In case there is no solution, return an empty array

return new int\[\] {};

}

}

**Complexity Analysis**

*   Time complexity: _O_(_n_).We traverse the list containing _n_ elements exactly twice. Since the hash table reduces the lookup time to _O_(1), the overall time complexity is _O_(_n_).
    
*   Space complexity: _O_(_n_).The extra space required depends on the number of items stored in the hash table, which stores exactly _n_ elements.
    

Approach 3: One-pass Hash Table

**Algorithm**

It turns out we can do it in one-pass. While we are iterating and inserting elements into the hash table, we also look back to check if current element's complement already exists in the hash table. If it exists, we have found a solution and return the indices immediately.

**Implementation**

class Solution {

public int\[\] twoSum(int\[\] nums, int target) {

Map map = new HashMap<>();

for (int i = 0; i < nums.length; i++) {

int complement = target - nums\[i\];

if (map.containsKey(complement)) {

return new int\[\] { map.get(complement), i };

}

map.put(nums\[i\], i);

}

// Return an empty array if no solution is found

return new int\[\] {};

}

}

**Complexity Analysis**

*   Time complexity: _O_(_n_).We traverse the list containing _n_ elements only once. Each lookup in the table costs only _O_(1) time.
    
*   Space complexity: _O_(_n_).The extra space required depends on the number of items stored in the hash table, which stores at most _n_ elements.
