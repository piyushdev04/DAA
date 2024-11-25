Time Complexity: O(logn)
Input:

A sorted array arr[] of size n.
The target element target to search for.
Initialization:

Set low = 0 (start index of the array).
Set high = n - 1 (end index of the array).
Recursive Steps:

Calculate the middle index:
mid
=
low
+
high
−
low
2
mid=low+ 
2
high−low
​
 
Compare the middle element arr[mid] with the target:
Case 1: If arr[mid] == target, return mid (target found).
Case 2: If arr[mid] > target, search in the left subarray:
binarySearch(arr, low, mid - 1, target)
binarySearch(arr, low, mid - 1, target)
Case 3: If arr[mid] < target, search in the right subarray:
binarySearch(arr, mid + 1, high, target)
binarySearch(arr, mid + 1, high, target)
Base Condition:

If low > high, return -1 (target not found in the array).
Output:

The index of the target element if found, otherwise -1.