import java.util.Scanner;

public class BinarySearch {

    public static int binarySearch(int[] arr, int low, int high, int target) {
        if (low <= high) {
            int mid = low + (high - low) / 2; 
            
            if (arr[mid] == target) {
                return mid;
            }
            
            if (target < arr[mid]) {
                return binarySearch(arr, low, mid - 1, target);
            }
            
            return binarySearch(arr, mid + 1, high, target);
        }
        
        return -1;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the size of the array: ");
        int n = scanner.nextInt();
        int[] arr = new int[n];
        
        System.out.println("Enter " + n + " sorted elements:");
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        
        System.out.print("Enter the target element to search: ");
        int target = scanner.nextInt();
        
        int result = binarySearch(arr, 0, n - 1, target);

        if (result == -1) {
            System.out.println("Element not found in the array.");
        } else {
            System.out.println("Element found at index: " + result);
        }

        scanner.close();
    }
}