```java
class Solution {
    // Function to detect cycle in an undirected graph.
    public boolean isCycle(int V, ArrayList<ArrayList<Integer>> adj) {
        Set<Integer> vis=new HashSet<>();
        
        for(int i=0;i<V;i++){
            if(!vis.contains(i) && isCycleDFS(i,-1,adj,vis))    
                return true;
        }
        
        return false;
    }
    public boolean isCycleDFS(int node,int parent,ArrayList<ArrayList<Integer>> adj,
                    Set<Integer> vis){
        vis.add(node);
        
        for(int it: adj.get(node)){
            if(!vis.contains(it)){
                if(isCycleDFS(it,node,adj,vis)==true)  return true;
            }else if(it!=parent)  return true;
        }
        
        return false;
    }
}
```
