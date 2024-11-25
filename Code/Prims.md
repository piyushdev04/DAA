import java.util.Arrays;
import java.util.Scanner;

public class PrimsAlgorithm {

    // Function to find the vertex with the minimum key value that is not included in MST
    public static int findMinKeyVertex(int[] key, boolean[] mstSet, int vertices) {
        int min = Integer.MAX_VALUE, minIndex = -1;

        for (int v = 0; v < vertices; v++) {
            if (!mstSet[v] && key[v] < min) {
                min = key[v];
                minIndex = v;
            }
        }
        return minIndex;
    }

    // Function to print the MST
    public static void printMST(int[] parent, int[][] graph, int vertices) {
        System.out.println("Edge \tWeight");
        for (int i = 1; i < vertices; i++) {
            System.out.println(parent[i] + " - " + i + "\t" + graph[i][parent[i]]);
        }
    }

    // Function to implement Prim's Algorithm
    public static void primMST(int[][] graph, int vertices) {
        int[] parent = new int[vertices]; // To store the MST
        int[] key = new int[vertices];   // To store minimum weights
        boolean[] mstSet = new boolean[vertices]; // To track included vertices

        // Initialize all keys to infinity and mstSet to false
        Arrays.fill(key, Integer.MAX_VALUE);
        Arrays.fill(mstSet, false);

        // Start with the first vertex
        key[0] = 0;       // First vertex is picked first
        parent[0] = -1;   // First node is always the root of MST

        // The MST will have 'vertices' vertices
        for (int count = 0; count < vertices - 1; count++) {
            // Pick the minimum key vertex not yet included in MST
            int u = findMinKeyVertex(key, mstSet, vertices);

            // Add the picked vertex to the MST set
            mstSet[u] = true;

            // Update the key and parent index of adjacent vertices
            for (int v = 0; v < vertices; v++) {
                // Update key[v] only if graph[u][v] is smaller than key[v]
                if (graph[u][v] != 0 && !mstSet[v] && graph[u][v] < key[v]) {
                    parent[v] = u;
                    key[v] = graph[u][v];
                }
            }
        }

        // Print the constructed MST
        printMST(parent, graph, vertices);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input number of vertices
        System.out.print("Enter the number of vertices: ");
        int vertices = scanner.nextInt();

        // Input adjacency matrix of the graph
        int[][] graph = new int[vertices][vertices];
        System.out.println("Enter the adjacency matrix (weights of edges, 0 for no edge):");
        for (int i = 0; i < vertices; i++) {
            for (int j = 0; j < vertices; j++) {
                graph[i][j] = scanner.nextInt();
            }
        }

        // Execute Prim's Algorithm
        primMST(graph, vertices);

        scanner.close();
    }
}