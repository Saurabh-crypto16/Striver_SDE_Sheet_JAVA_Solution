```java
/*
Brute: For each i find the next smaller element index and last smaller index and area will be
       (next smaller idx - last smaller idx + 1) * curr height
*/

class Solution {
    public int largestRectangleArea(int[] h) {
        Stack<Integer> st=new Stack<>();
        int leftSmall[]=new int[h.length];
        int rightSmall[]=new int[h.length];
        
        //finding left smaller element for each element
        for(int i=0;i<h.length;i++){
            while(!st.isEmpty() && h[st.peek()]>=h[i]){
                st.pop();
            }
            
            if(!st.isEmpty()) leftSmall[i]=st.peek()+1;
            else    leftSmall[i]=0;
            st.push(i);
        }
        
        st.clear();
        
        //finding right smaller element for each element
        for(int i=h.length-1;i>=0;i--){
            while(!st.isEmpty() && h[st.peek()]>=h[i]){
                st.pop();
            }
            
            if(!st.isEmpty()) rightSmall[i]=st.peek()-1;
            else    rightSmall[i]=h.length-1;
            st.push(i);
        }
        
        int maxA=0;
        for(int i=0;i<h.length;i++){
            maxA=Math.max(maxA,(rightSmall[i]-leftSmall[i]+1)*h[i]);
        }
        
        return maxA;
    }
}

/*
Better: Store the index of linearly increasing elements of array in the stack 
eg: for arr=[2,1,5,6,2,3] at end stack=[2,5,6]

for each i if height[i] >= st.peek() then 
height = heights[st.pop()]
width will be i if stack is empty else i-st.peek()-1
*/

class Solution {
    public int largestRectangleArea(int[] heights) {
        Stack<Integer> st=new Stack<>();
        int maxA=0;
        
        for(int i=0;i<=heights.length;i++){
            while(!st.isEmpty() && (i==heights.length || heights[st.peek()]>=heights[i])){
                int ht=heights[st.pop()];
                int width=0;
                
                if(st.isEmpty())    width=i;
                else    width=i-st.peek()-1;
                
                maxA=Math.max(maxA,width*ht);
            }
            
            st.push(i);
        }
        
        return maxA;
    }
}
```
