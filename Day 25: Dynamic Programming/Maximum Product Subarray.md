```java
import java.util.ArrayList;

public class Solution {
	public static int maximumProduct(ArrayList<Integer> arr, int n) {
		// Write your code here.
        long ans=Long.MIN_VALUE;
        
        long cprod=1;
        for(int i=0;i<n;i++){
            cprod*=arr.get(i);
            ans=Math.max(ans,cprod);
            if(arr.get(i)==0){
                cprod=1;
            }
        }
        
        cprod=1;
        for(int i=n-1;i>=0;i--){
            cprod*=arr.get(i);
            ans=Math.max(ans,cprod);
            if(arr.get(i)==0){
                cprod=1;
            }
        }
        
        return (int)ans;
	}
}
```
