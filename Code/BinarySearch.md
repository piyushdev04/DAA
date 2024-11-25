import java.util.Scanner;

public class BinarySearch {

    // Function to perform binary search
    public static int binarySearch(int[] arr, int low, int high, int target) {
        if (low <= high) {
            int mid = low + (high - low) / 2; // To avoid overflow
            
            // Check if the target is present at the middle
            if (arr[mid] == target) {
                return mid;
            }

            // If the target is smaller than mid, it can only be in the left subarray
            if (target < arr[mid]) {
                return binarySearch(arr, low, mid - 1, target);
            }

            // Otherwise, it must be in the right subarray
            return binarySearch(arr, mid + 1, high, target);
        }

        // Target is not present in the array
        return -1;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input array size
        System.out.print("Enter the size of the array: ");
        int n = scanner.nextInt();
        int[] arr = new int[n];

        // Input array elements (sorted)
        System.out.println("Enter " + n + " sorted elements:");
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }

        // Input target element
        System.out.print("Enter the target element to search: ");
        int target = scanner.nextInt();

        // Perform binary search
        int result = binarySearch(arr, 0, n - 1, target);

        // Output the result
        if (result == -1) {
            System.out.println("Element not found in the array.");
        } else {
            System.out.println("Element found at index: " + result);
        }

        scanner.close();
    }
}