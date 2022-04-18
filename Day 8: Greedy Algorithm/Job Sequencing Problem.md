```java
class Solution{
    int[] JobScheduling(Job arr[], int n){
        //sorting based on decreasing profit
        Arrays.sort(arr,(a,b) -> b.profit-a.profit);
        
        int max_deadline=0;
        for(Job j: arr){
            max_deadline=Math.max(max_deadline,j.deadline);
        }
        
        int res[]=new int[max_deadline+1];
        Arrays.fill(res,-1);
        int countJobs=0,jobProfit=0;
        
        for(int i=0;i<n;i++){
            for(int j=arr[i].deadline;j>0;j--){
                //finding the 1st free slot from arr[i].deadline to 1
                if(res[j]==-1){
                    res[j]=i;
                    countJobs++;
                    jobProfit+=arr[i].profit;
                    break;
                }
            }
        }
        
        int ans[]=new int[2];
        ans[0]=countJobs;
        ans[1]=jobProfit;
        
        return ans;
    }
}
```
