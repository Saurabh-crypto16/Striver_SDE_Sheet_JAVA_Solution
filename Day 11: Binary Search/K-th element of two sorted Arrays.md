```java
//User function Template for Java
//Same approach as median of 2 sorted arrays
//partition the array into left and right parts and the max of left part will be ans

class Solution {
    public long kthElement( int arr1[], int arr2[], int n, int m, int k) {
        if(n>m){
            return kthElement(arr2,arr1,m,n,k);
        }
        
        int lo=Math.max(0,k-m),hi=Math.min(k,n);
        
        while(lo<=hi){
            //index of last element from nums1 in left half
            int cut1=lo+(hi-lo)/2;
            //index of last element from nums2 in left half
            int cut2=k-cut1;
            
            //finding particular element
            int l1=cut1==0 ? Integer.MIN_VALUE : arr1[cut1-1];
            int l2=cut2==0 ? Integer.MIN_VALUE : arr2[cut2-1];
            int r1=cut1==n ? Integer.MAX_VALUE : arr1[cut1];
            int r2=cut2==m ? Integer.MAX_VALUE : arr2[cut2];
            
            if(l1<=r2 && l2<=r1){
                return Math.max(l1,l2);
            }else if(l1>r2){
                hi=cut1-1;
            }else{
                lo=cut1+1;
            }
        }
        
        return 1;
    }
}
```
