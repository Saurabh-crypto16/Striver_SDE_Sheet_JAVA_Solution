```java
/*
Brute: Generate all subarrays and find xor of elements of each subarray 
Best: x ^ k = xor 
      => x = xor ^ k
      Sor at every idx we check if there exists a subarray with xor value x(xor ^ k) if so we count it 
*/
public class Solution {
    public int solve(ArrayList<Integer> A, int B) {
        //(previous elements xor,count of subarray with xor)
        HashMap<Integer,Integer> freq=new HashMap<>();
        int count=0,xor=0,n=A.size();

        for(int i: A){
            xor^=i;
            if(freq.get(xor^B)!=null){
                //y=xor^B if it exists we add the count of y to ans
                count+=freq.get(xor^B);
            }
            if(xor==B){
                count++;
            }
            
            //adding new xor count or increment old count by 1
            freq.put(xor,freq.getOrDefault(xor,0)+1);
        }
        return count;
    }
}

```
