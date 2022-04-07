```java
/*
calculate the sum at every idx.
If sum==0 then check if its the maxlen
if sum != 0 then 
check if the sum already exists in map if so substract the distance between curr idx and map idx for sum
if sum not in map add it as key and the idx as value
*/

import java.util.*;

public class Solution {
	public static int LongestSubsetWithZeroSum(ArrayList<Integer> arr) {
		HashMap<Integer,Integer> map=new HashMap<>();
        
        int sum=0,maxlen=0;
        for(int i=0;i<arr.size();i++){
            sum+=arr.get(i);
            if(sum==0){
                maxlen=Math.max(maxlen,i+1);
            }else if(map.containsKey(sum)){
                maxlen=Math.max(maxlen,i-map.get(sum));
            }else{
                map.put(sum,i);
            }
        }
        
        return maxlen;
	}
}
```
