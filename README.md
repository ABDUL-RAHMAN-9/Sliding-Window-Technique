# Sliding-Window-Technique

Sliding Window problems involve moving a fixed or variable-size window through a data structure, typically an array or string, to solve problems efficiently based on continuous subsets of elements. This technique is used when we need to find subarrays or substrings according to a given set of conditions.

<div align='center'>

  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240312122853/Sliding-Window-Technique-copy-(1).webp" width=400>
</div>

## What is Sliding Window Technique?

<h3><i>
  Sliding Window Technique is a method used to efficiently solve problems that involve defining a window or range in the input data (arrays or strings) and then moving that window across the data to perform some operation within the window. This technique is commonly used in algorithms like finding subarrays with a specific sum, finding the longest substring with unique characters, or solving problems that require a fixed-size window to process elements efficiently.
</i></h3>



- Let’s take an example to understand this properly, say we have an array of size N and also an integer K. Now, we have to calculate the maximum sum of a subarray having size exactly K. Now how should we approach this problem?

- One way to do this by taking each subarray of size K from the array and find out the maximum sum of these subarrays. This can be done using Nested loops which will result into O(N2) Time Complexity.

- But can we optimize this approach?

- The answer is Yes, instead of taking each K sized subarray and calculating its sum, we can just take one K size subarray from 0 to K-1 index and calculate its sum now shift our range one by one along with the iterations and update the result, like in next iteration increase the left and right pointer and update the previous sum as shown in the below image:



<div align='center'>

  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240306112433/sliding-window-1.webp" width=400>
</div>


Now follow this method for each iteration till we reach the end of the array:


<div align='center'>

  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240306112450/sliding-window-technique-2.webp" width=400>
</div>


- So, we can see that instead of recalculating the sum of each K sized subarray we are using previous window of size K and using its results we update the sum and shift the window right by moving left and right pointers, this operation is optimal because it take O(1) time to shift the range instead of recalculating.

- This approach of shifting the pointers and calculating the results accordingly is known as Sliding window Technique.


## Use Cases of Sliding Window Technique:
1. To find the maximum sum of all subarrays of size K:
   
- Given an array of integers of size ‘n’, Our aim is to calculate the maximum sum of ‘k’ consecutive elements in the array.

  - Input  : arr[] = {100, 200, 300, 400}, k = 2
  - Output : 700


  - Input  : arr[] = {1, 4, 2, 10, 23, 3, 1, 0, 20}, k = 4 
  - Output : 39
- We get maximum sum by adding subarray {4, 2, 10, 23} of size 4.


  - Input  : arr[] = {2, 3}, k = 3
  - Output : Invalid
- There is no subarray of size 3 as size of whole array is 2.


- <h2>Naïve Approach</h2>: So, let’s analyze the problem with Brute Force Approach. We start with the first index and sum till the kth element. We do it for all possible consecutive blocks or groups of k elements. This method requires a nested for loop, the outer for loop starts with the starting element of the block of k elements, and the inner or the nested loop will add up till the kth element.

## Below is the implementation of the above approach: 

```
// O(n*k) solution for finding maximum sum of
// a subarray of size k
#include <bits/stdc++.h>
using namespace std;

// Returns maximum sum in a subarray of size k.
int maxSum(int arr[], int n, int k)
{
    // Initialize result
    int max_sum = INT_MIN;

    // Consider all blocks starting with i.
    for (int i = 0; i < n - k + 1; i++) {
        int current_sum = 0;
        for (int j = 0; j < k; j++)
            current_sum = current_sum + arr[i + j];

        // Update result if required.
        max_sum = max(current_sum, max_sum);
    }

    return max_sum;
}

// Driver code
int main()
{
    int arr[] = { 1, 4, 2, 10, 2, 3, 1, 0, 20 };
    int k = 4;
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << maxSum(arr, n, k);
    return 0;
}
```

## Output

```
24
```

## Complexity:

```
Time complexity: O(k*n) as it contains two nested loops.
Auxiliary Space: O(1)
```



















