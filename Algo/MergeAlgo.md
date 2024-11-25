Time complexity: O(nlogn)

Algorithm for Merge Sort
Input:

An unsorted array arr[] of size n.
Divide:

Recursively split the array into two halves:
Left subarray: arr[left..mid].
Right subarray: arr[mid+1..right].
Conquer:

Recursively sort the left and right subarrays.
Combine:

Merge the sorted left and right subarrays using the merge() function.
Output:

The sorted array.