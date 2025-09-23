---

Count Even and Odd Numbers in an Array (Easy)

Problem Statement:-

Given an array of integers, count the number of even and odd numbers present in the array.


---

Brute Force Approach:

Step-by-step explanation:

1. Initialize two counters, evenCount and oddCount.


2. Traverse the array element by element.


3. If the element is divisible by 2, increment evenCount. Otherwise, increment oddCount.


4. Return or print both counts.



Java

public class CountEvenOdd {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6};
        int evenCount = 0, oddCount = 0;
        
        for (int num : arr) {
            if (num % 2 == 0)
                evenCount++;
            else
                oddCount++;
        }
        
        System.out.println("Even numbers: " + evenCount);
        System.out.println("Odd numbers: " + oddCount);
    }
}

C++

#include <iostream>
using namespace std;

int main() {
    int arr[] = {1, 2, 3, 4, 5, 6};
    int n = sizeof(arr)/sizeof(arr[0]);
    int evenCount = 0, oddCount = 0;
    
    for(int i = 0; i < n; i++) {
        if(arr[i] % 2 == 0)
            evenCount++;
        else
            oddCount++;
    }
    
    cout << "Even numbers: " << evenCount << endl;
    cout << "Odd numbers: " << oddCount << endl;
    
    return 0;
}


---

Optimal Approach:

The brute force method is already optimal because:

Time Complexity: O(n) → one pass through the array.

Space Complexity: O(1) → only two counters are used.



---
