```java

public class Solution {

	public static int lcs(String s, String t) {
		int dp[][]=new int[s.length()+1][t.length()+1];
        
        for(int i=dp.length-2;i>=0;i--){
            for(int j=dp[0].length-2;j>=0;j--){
                if(s.charAt(i)==t.charAt(j)){
                    dp[i][j]=1+dp[i+1][j+1];
                }else{
                    dp[i][j]=Math.max(dp[i][j+1],dp[i+1][j]);
                }
            }
        }
        
        return dp[0][0];
    }

}
```
