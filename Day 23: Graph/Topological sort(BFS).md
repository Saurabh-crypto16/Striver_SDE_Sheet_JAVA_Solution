```java
class Solution{
    //Function to return list containing vertices in Topological order. 
    static int[] topoSort(int V, ArrayList<ArrayList<Integer>> adj) {
        int indeg[]=new int[V];
        
        for(int i=0;i<V;i++){
            for(int it: adj.get(i)){
                indeg[it]++;
            }
        }
        
        ArrayList<Integer> ans=new ArrayList<>();
        for(int i=0;i<V;i++){
            if(indeg[i]==0) ans.add(i);
        }
        
        for(int i=0;i<ans.size();i++){
            for(int j: adj.get(ans.get(i))){
                if(--indeg[j]==0)   ans.add(j);
            }
        }
        
        return ans.stream().mapToInt(i -> i).toArray();
    }
}

```
