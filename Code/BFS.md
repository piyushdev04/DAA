import java.util.*;

public class BreadthFirstTraversal {

    static class Graph {
        private int vertices; 
        private LinkedList<Integer>[] adjacencyList; 

        
        Graph(int vertices) {
            this.vertices = vertices;
            adjacencyList = new LinkedList[vertices];
            for (int i = 0; i < vertices; i++) {
                adjacencyList[i] = new LinkedList<>();
            }
        }

        
        void addEdge(int src, int dest) {
            adjacencyList[src].add(dest);
            adjacencyList[dest].add(src); 
        }

        
        void BFS(int startVertex) {
            
            boolean[] visited = new boolean[vertices];
            Queue<Integer> queue = new LinkedList<>();

            
            visited[startVertex] = true;
            queue.add(startVertex);

            System.out.println("Breadth-First Traversal starting from vertex " + startVertex + ":");
            while (!queue.isEmpty()) {
                
                int currentVertex = queue.poll();
                System.out.print(currentVertex + " ");

                
                for (int neighbor : adjacencyList[currentVertex]) {
                    if (!visited[neighbor]) {
                        visited[neighbor] = true;
                        queue.add(neighbor);
                    }
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        
        System.out.print("Enter the number of vertices: ");
        int vertices = scanner.nextInt();
        System.out.print("Enter the number of edges: ");
        int edges = scanner.nextInt();

        
        Graph graph = new Graph(vertices);

        
        System.out.println("Enter the edges (source destination):");
        for (int i = 0; i < edges; i++) {
            int src = scanner.nextInt();
            int dest = scanner.nextInt();
            graph.addEdge(src, dest);
        }

        
        System.out.print("Enter the starting vertex for BFS: ");
        int startVertex = scanner.nextInt();

        
        graph.BFS(startVertex);

        scanner.close();
    }
}
