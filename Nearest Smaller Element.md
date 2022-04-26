```java
public class Solution {
    public ArrayList<Integer> prevSmaller(ArrayList<Integer> A) {
        ArrayList<Integer> ans=new ArrayList<Integer>();
        Stack<Integer> st=new Stack<>();

        for(int num: A){
            //keep poping stack till its top is less than curr
            while(!st.isEmpty() && st.peek()>=num){
                st.pop();
            }

            if(!st.isEmpty()){
                ans.add(st.peek());
            }else{
                ans.add(-1);
            }

            st.push(num);
        }

        return ans;
    }
}

```
