Time Complexity: O(nlogn)

Algorithm for Heap Sort
Input:

An unsorted array arr[] of size n.
Steps:

Build a max heap from the input array.
Start from the last non-leaf node and call heapify() for each node.
Swap the root of the heap (largest element) with the last element in the heap.
Reduce the heap size by 1 and call heapify() on the root.
Repeat until the heap size is reduced to 1.
Output:

The sorted array.