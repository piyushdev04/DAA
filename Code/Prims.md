import java.util.Arrays;
import java.util.Scanner;

public class PrimsAlgorithm {

    
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

    
    public static void printMST(int[] parent, int[][] graph, int vertices) {
        System.out.println("Edge \tWeight");
        for (int i = 1; i < vertices; i++) {
            System.out.println(parent[i] + " - " + i + "\t" + graph[i][parent[i]]);
        }
    }

    
    public static void primMST(int[][] graph, int vertices) {
        int[] parent = new int[vertices]; 
        int[] key = new int[vertices];   
        boolean[] mstSet = new boolean[vertices]; 

        
        Arrays.fill(key, Integer.MAX_VALUE);
        Arrays.fill(mstSet, false);

        
        key[0] = 0;      
        parent[0] = -1;  

        
        for (int count = 0; count < vertices - 1; count++) {
            
            int u = findMinKeyVertex(key, mstSet, vertices);

            
            mstSet[u] = true;

            
            for (int v = 0; v < vertices; v++) {
                
                if (graph[u][v] != 0 && !mstSet[v] && graph[u][v] < key[v]) {
                    parent[v] = u;
                    key[v] = graph[u][v];
                }
            }
        }

        
        printMST(parent, graph, vertices);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        
        System.out.print("Enter the number of vertices: ");
        int vertices = scanner.nextInt();

        
        int[][] graph = new int[vertices][vertices];
        System.out.println("Enter the adjacency matrix (weights of edges, 0 for no edge):");
        for (int i = 0; i < vertices; i++) {
            for (int j = 0; j < vertices; j++) {
                graph[i][j] = scanner.nextInt();
            }
        }

        
        primMST(graph, vertices);

        scanner.close();
    }
}