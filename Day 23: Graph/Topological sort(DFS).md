```java
class Solution{
    //Function to return list containing vertices in Topological order. 
    static int[] topoSort(int V, ArrayList<ArrayList<Integer>> adj) {
        Stack<Integer> st=new Stack<>();
        int ans[]=new int[V];
        int vis[]=new int[V];
        
        for(int i=0;i<V;i++){
            if(vis[i]==0){
                findTopoSort(adj,st,i,vis);
            }
        }
        
        int idx=0;
        while(!st.isEmpty()){
            ans[idx++]=st.pop();
        }
        
        return ans;
    }
    public static void findTopoSort(ArrayList<ArrayList<Integer>> adj,Stack<Integer> st,
                            int node,int[] vis){
        vis[node]=1;
        
        for(int i: adj.get(node)){
            if(vis[i]==0){
                findTopoSort(adj,st,i,vis);
            }
        }
        
        st.push(node);
    }
}
```
