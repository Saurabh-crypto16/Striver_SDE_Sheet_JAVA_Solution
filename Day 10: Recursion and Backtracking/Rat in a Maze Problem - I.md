```java
// m is the given matrix and n is the order of matrix
class Solution {
    static ArrayList<String> res;
    static int vis[][];
    public static ArrayList<String> findPath(int[][] m, int n) {
        vis=new int[n][n];
        res=new ArrayList<>();
        
        if(m[0][0]==1)  
            solve(0,0,"",m,n);
        
        return res;
    }
    public static void solve(int i,int j,String path,int[][] m,int n){
        if(i==n-1 && j==n-1){
            res.add(path);
            return;
        }
        
        //down
        if(i+1<n && vis[i+1][j]==0 && m[i+1][j]==1){
            vis[i][j]=1;
            solve(i+1,j,path+"D",m,n);
            vis[i][j]=0;
        }
        
        //left
        if(j-1>=0 && vis[i][j-1]==0 && m[i][j-1]==1){
            vis[i][j]=1;
            solve(i,j-1,path+"L",m,n);
            vis[i][j]=0;
        }
        
        //right
        if(j+1<n && vis[i][j+1]==0 && m[i][j+1]==1){
            vis[i][j]=1;
            solve(i,j+1,path+"R",m,n);
            vis[i][j]=0;
        }
        
        //up
        if(i-1>=0 && vis[i-1][j]==0 && m[i-1][j]==1){
            vis[i][j]=1;
            solve(i-1,j,path+"U",m,n);
            vis[i][j]=0;
        }
    }
}
```
