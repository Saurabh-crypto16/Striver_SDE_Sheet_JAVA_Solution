```java
class solve 
{
    //Function to determine if graph can be coloured with at most M colours such
    //that no two adjacent vertices of graph are coloured with same colour.
    //i is starting node
    public static boolean graphColoring(List<Integer>[] G, int[] color, int i, int m) 
    {
        return solve(i,G,color,G.length,m);
    }
    public static boolean solve(int node,List<Integer>[] G,int[] color,int n,int m){
        if(node==n)     //if we reach last node from first node 
            return true;
        
        //trying every possible color    
        for(int i=1;i<=m;i++){
            if(isSafe(node,G,color,n,i)){
                //if safe then color it
                color[node]=i;
                
                if(solve(node+1,G,color,G.length,m))
                    return true;
                
                //if not true then uncolor the node
                color[node]=0;
            }
        }
        
        return false;
    }
    public static boolean isSafe(int node,List<Integer>[] G,int[] color,int n,int col){
        //if any of the neighbors have same color as node
        for(int it: G[node]){
            if(color[it]==col)  return false;
        }
        
        return true;
    }
}
```
