Time Complexity: O(n^2)

Algorithm for Quick Sort
Input:

Array arr[] with size n, and indices low and high which define the subarray being sorted.

Steps:

- If low<high:
 - Partition the array, returning the pivot index.
 - Recursively sort the subarrays before and after the pivot.

Partitioning:

- Choose a pivot (last element in the subarray).
- Rearrange the array such that elements smaller than the pivot are on the left, and elements greater than the pivot are on the right.
- Place the pivot at its correct sorted position and return its index.

Output:

Sorted array.