import java.util.Arrays;
import java.util.Scanner;

class Edge implements Comparable<Edge> {
    int src, dest, weight;

    public int compareTo(Edge other) {
        return this.weight - other.weight;
    }
}

public class KruskalsAlgorithm {

    
    static class Subset {
        int parent, rank;
    }

    
    public static int find(Subset[] subsets, int i) {
        if (subsets[i].parent != i) {
            subsets[i].parent = find(subsets, subsets[i].parent);
        }
        return subsets[i].parent;
    }

    
    public static void union(Subset[] subsets, int x, int y) {
        int rootX = find(subsets, x);
        int rootY = find(subsets, y);

        if (subsets[rootX].rank < subsets[rootY].rank) {
            subsets[rootX].parent = rootY;
        } else if (subsets[rootX].rank > subsets[rootY].rank) {
            subsets[rootY].parent = rootX;
        } else {
            subsets[rootY].parent = rootX;
            subsets[rootX].rank++;
        }
    }

    
    public static void kruskalMST(Edge[] edges, int vertices, int edgeCount) {
        
        Edge[] result = new Edge[vertices - 1];
        int e = 0; 
        int i = 0; 

        
        Arrays.sort(edges);

        
        Subset[] subsets = new Subset[vertices];
        for (int v = 0; v < vertices; v++) {
            subsets[v] = new Subset();
            subsets[v].parent = v;
            subsets[v].rank = 0;
        }

        
        while (e < vertices - 1 && i < edgeCount) {
            Edge nextEdge = edges[i++];

            int x = find(subsets, nextEdge.src);
            int y = find(subsets, nextEdge.dest);

            
            if (x != y) {
                result[e++] = nextEdge;
                union(subsets, x, y);
            }
        }

        
        System.out.println("Edge \tWeight");
        for (i = 0; i < e; i++) {
            System.out.println(result[i].src + " - " + result[i].dest + "\t" + result[i].weight);
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        
        System.out.print("Enter the number of vertices: ");
        int vertices = scanner.nextInt();
        System.out.print("Enter the number of edges: ");
        int edgeCount = scanner.nextInt();


        Edge[] edges = new Edge[edgeCount];
        System.out.println("Enter the edges (source, destination, weight):");
        for (int i = 0; i < edgeCount; i++) {
            edges[i] = new Edge();
            edges[i].src = scanner.nextInt();
            edges[i].dest = scanner.nextInt();
            edges[i].weight = scanner.nextInt();
        }


        kruskalMST(edges, vertices, edgeCount);

        scanner.close();
    }
}