```java
public class Solution {
    public static long getInversions(long arr[], int n) {
        // Write your code here.
        return mergeSort(arr,new long[n],0,n-1);
    }
    public static long mergeSort(long arr[],long temp[],int left,int right){
        int mid;
        long inv_cnt=0;
        
        if(right>left){
            mid=left+(right-left)/2;
        	
            //breaking the array
            inv_cnt+=mergeSort(arr,temp,left,mid);
            inv_cnt+=mergeSort(arr,temp,mid+1,right);
            
            //merging
            inv_cnt+=merge(arr,temp,left,mid+1,right);
        }
        
        return inv_cnt;
    }
    public static long merge(long arr[],long temp[],int left,int mid,int right){
        //i=idx of left subarray
        //j=idx of right subarray
        //k=idx of merged array
        int i=left,j=mid,k=left;
        long inv_cnt=0;
        
        while((i<=mid-1) && (j<=right)){
            if(arr[i]<=arr[j]){
                //if left is smaller than right
                temp[k++]=arr[i++];
            }else{
                temp[k++]=arr[j++];
                
                //number of elements right of i upto mid in arr
                inv_cnt+=(mid-i);
            }
        }
        
        while(i<=mid-1)	temp[k++]=arr[i++];
        
        while(j<=right)	temp[k++]=arr[j++];
        
        //copying back sorted val to original array
        for(i=left;i<=right;i++){
            arr[i]=temp[i];
        }
        
        return inv_cnt;
    }
}
```
