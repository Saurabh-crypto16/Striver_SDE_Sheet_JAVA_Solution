```java
import java.util.*;

class Node implements Comparator<Node>{
    private int v;
    private int weight;
    
    Node(int _v, int _w) { v = _v; weight = _w; }
    Node() {}
    
    int getV() { return v; }
    int getWeight() { return weight; }
    
    @Override
    public int compare(Node node1, Node node2) { 
        if (node1.weight < node2.weight) 	return -1; 
        if (node1.weight > node2.weight) 	return 1; 
        return 0; 
    } 
}
public class Solution {
	public static ArrayList<Integer> dijkstra(ArrayList<ArrayList<Integer>> vec, int vertices, 
											int edges, int s){
		ArrayList<ArrayList<Node>> adj=new ArrayList<>();
		for(int i=0;i<vertices;i++){
			adj.add(new ArrayList<>());
		}
		
		//creating graph
		for(ArrayList<Integer> edge: vec){
			int u=edge.get(0),v=edge.get(1),w=edge.get(2);
			adj.get(u).add(new Node(v,w));
			adj.get(v).add(new Node(u,w));
		}
		
		int dist[]=new int[vertices];
		Arrays.fill(dist,Integer.MAX_VALUE);
		dist[s]=0;
		PriorityQueue<Node> pq = new PriorityQueue<Node>(vertices, new Node());
        pq.add(new Node(s, 0));
        
        while(pq.size() > 0) {
            Node node = pq.poll();
            
            for(Node it: adj.get(node.getV())) {
                if(dist[node.getV()] + it.getWeight() < dist[it.getV()]) {
                    dist[it.getV()] = dist[node.getV()] + it.getWeight(); 
                    pq.add(new Node(it.getV(), dist[it.getV()]));
                }
            }
        }
		
		ArrayList<Integer> ans = new ArrayList<>();
        for(int i: dist)	ans.add(i);
		
		return ans;
	}
}
```
