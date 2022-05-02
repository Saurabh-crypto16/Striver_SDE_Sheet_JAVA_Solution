```java
import java.util.*;

public class Solution {
    public static List<List<Integer>> stronglyConnectedComponents(int n, int[][] edges) {
        List<List<Integer>> adj=new ArrayList<>();
		List<List<Integer>> transpose=new ArrayList<>();
		List<List<Integer>> ans=new ArrayList<>();
		
		for(int i=0;i<n;i++){
			adj.add(new ArrayList<Integer>());
			transpose.add(new ArrayList<Integer>());
		}
		
		//creating graph
		for(int e[]: edges){
			adj.get(e[1]).add(e[0]);
		}
		
		//find topo sort for getting nodes in decreasing order of access time
		Stack<Integer> st=new Stack<>();
		int vis[]=new int[n];
		for(int i=0;i<n;i++)	
			if(vis[i]==0)	topoSort(i,vis,st,adj);
		
		//finding transpose of adj
		Arrays.fill(vis,0);
		for(int i=0;i<n;i++){
			for(int it: adj.get(i)){
				transpose.get(it).add(i);
			}
		}
		
		while(!st.isEmpty()){
			int node=st.pop();
			if(vis[node]==0){
				List<Integer> list=new ArrayList<>();
				revDfs(node,transpose,vis,list);
				ans.add(new ArrayList<>(list));
			}
		}
		
		return ans;
    }
	public static void topoSort(int i,int[] vis,Stack<Integer> st,List<List<Integer>> adj){
		vis[i]=1;
		
		for(int it: adj.get(i)){
			if(vis[it]==0)	topoSort(it,vis,st,adj);
		}
		
		st.push(i);
	}
	public static void revDfs(int node,List<List<Integer>> transpose,int[] vis,
							  List<Integer> list){
		vis[node]=1;
		list.add(node);
		
		for(int it: transpose.get(node)){
			if(vis[it]==0)	revDfs(it,transpose,vis,list);
		}
	}
}
```
