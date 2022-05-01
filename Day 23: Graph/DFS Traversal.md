```java
/*
    Time Complexity     :   O((V * log(V)) + E)
    Space Complexity    :   O(V + E)

    Where 'V' is the number of vertex and 'E' is the number of edges in graph.
*/

import java.util.*;

public class Solution {
    private static void depthFirstSearchHelper(ArrayList<ArrayList<Integer>> graph, int currVertex, 
    						ArrayList<Integer> singleComponent, boolean[] visited) {
        visited[currVertex] = true;
        singleComponent.add(currVertex);
        
        for (int childVertex : graph.get(currVertex)) {
            // Check if the node is visited before or not.
            if(!visited[childVertex]) {
                depthFirstSearchHelper(graph, childVertex, singleComponent, visited);
            }
        }
    }

    public static ArrayList<ArrayList<Integer>> depthFirstSearch(int v, int e, 
								ArrayList<ArrayList<Integer>> edges) {
        ArrayList<ArrayList<Integer>> adjList = new ArrayList<>(v);
        for (int i = 0; i < v; i++) {
            adjList.add(new ArrayList<>());
        }

        for (int i = 0; i < e; i++) {
            int firstVertex = edges.get(i).get(0);
            int secondVertex = edges.get(i).get(1);
            
            ArrayList<Integer> list = adjList.get(firstVertex);
            list.add(secondVertex);
            
            list = adjList.get(secondVertex);
            list.add(firstVertex);
        }

        ArrayList<ArrayList<Integer>> components = new ArrayList<>();
        boolean visited[] = new boolean[v + 1];
        
        for (int vertex = 0; vertex < v; vertex++) {
            if (!visited[vertex]) {
                ArrayList<Integer> singleComponent = new ArrayList<>();
                depthFirstSearchHelper(adjList, vertex, singleComponent, visited);
                components.add(singleComponent);
            }
        }
        return components;
    }
}
```
