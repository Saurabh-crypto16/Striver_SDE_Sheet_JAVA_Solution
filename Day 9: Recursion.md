```java
class Solution{
    ArrayList<Integer> res;
    ArrayList<Integer> subsetSums(ArrayList<Integer> arr, int N){
        res=new ArrayList<>();
        bt(0,arr,new ArrayList<Integer>());
        
        return res;
    }
    public void bt(int curr,ArrayList<Integer> nums,ArrayList<Integer> list){
        res.add(sum(list));
        
        for(int i=curr;i<nums.size();i++){
            list.add(nums.get(i));
            bt(i+1,nums,list);
            list.remove(list.size()-1);
        }
    }
    public int sum(ArrayList<Integer> list){
        int sum=0;
        for(int i: list)    sum+=i;
        return sum;
    }
}
```
