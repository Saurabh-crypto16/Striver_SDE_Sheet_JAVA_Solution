```java
/*
Brute: Iterate over every element and store in an array sort it and then find the middle
*/

public class Solution {
    public int findMedian(ArrayList<ArrayList<Integer>> m) {
        int max = Integer.MIN_VALUE;
        int min = Integer.MAX_VALUE;
        int r=m.size(), c=m.get(0).size();
        
        //finding min and max value in matrix
        for(int i=0; i<r ; i++){
            if(m.get(i).get(0) < min)    min = m.get(i).get(0);
            if(m.get(i).get(c-1) > max)     max = m.get(i).get(c-1);
        }
        
        int ans=0;
        while(min<=max){
            int mid=min+(max-min)/2;

            //number of elements less than mid 
            int count=0;
            for(int i=0;i<r;i++){
                count+=(func(m.get(i),mid));
            }

            if(count<=(r*c)/2) {
                min=mid+1;
                ans=mid;
            }
            else max=mid-1;
        }
        
        return ans;
    }
    public int func(ArrayList<Integer> arr,int val){
        int len=0;
        int lo=0,hi=arr.size()-1;

        while(lo<=hi){
            int mid=lo+(hi-lo)/2;

            if(arr.get(mid)<val){
                len=mid+1;
                lo=mid+1;
            }else{
                hi=mid-1;
            }
        }

        return len;
    }
}

```
