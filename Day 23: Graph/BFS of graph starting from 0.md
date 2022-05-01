```java
class Solution {
    // Function to return Breadth First Traversal of given graph.
    public ArrayList<Integer> bfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj) {
        ArrayList<Integer> ans=new ArrayList<>();
        Set<Integer> vis=new HashSet<>();
        
        Queue<Integer> q=new LinkedList<>();
        q.offer(0);
        vis.add(0);
                
        while(!q.isEmpty()){
            int curr=q.poll();
            ans.add(curr);
                    
            for(int n: adj.get(curr)){
                if(!vis.contains(n)){
                    vis.add(n);
                    q.offer(n);
                }
            }
        }
        
        return ans;
    }
}
```
