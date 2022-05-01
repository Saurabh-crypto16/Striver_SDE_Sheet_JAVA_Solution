```java
/*
We use traverse using BfS and if we traverse a node that is node a parent to current node 
but is already visited then we conclude there exists a cycle
*/
class Solution {
    class Node{
        int first;
        int parent;
        Node(int first,int parent){
            this.first=first;
            this.parent=parent;
        }
    }
    // Function to detect cycle in an undirected graph.
    public boolean isCycle(int V, ArrayList<ArrayList<Integer>> adj) {
        Set<Integer> vis=new HashSet<>();
        
        for(int i=0;i<V;i++){
            if(!vis.contains(i) && isCycleBFS(adj,i,vis)){
                return true;
            }
        }
        
        return false;
    }
    public boolean isCycleBFS(ArrayList<ArrayList<Integer>> adj,int s,Set<Integer> vis){
        Queue<Node> q=new LinkedList<>();
        q.add(new Node(s,-1));
        vis.add(s);
        
        while(!q.isEmpty()){
            Node curr=q.poll();
            int node=curr.first;
            int par=curr.parent;
            
            for(int n: adj.get(node)){
                if(!vis.contains(n)){
                    q.add(new Node(n,node));
                    vis.add(n);
                }else if(n!=par){ //checking if neighbor visited node is node parent
                    return true;
                }
            }
        }
        
        return false;
    }
}
```
