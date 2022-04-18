```java
import java.util.*;

public class Solution {
    public static int calculateMinPatforms(int at[], int dt[], int n) {
        // Sort the arrival time and departure time seperately
		Arrays.sort(at);
		Arrays.sort(dt);
		
		int platform_needed=1,result=1;
		int i=1,j=0;	//i=arrival time pointer and j=departure time pointer 
		
		while(i<n && j<n){
			if(at[i]<=dt[j]){
				platform_needed++;
				i++;
			}else if(at[i]>dt[j]){
				platform_needed--;
				j++;
			}
			
			result=Math.max(result,platform_needed);
		}
		
		return result;
    }
}
```
