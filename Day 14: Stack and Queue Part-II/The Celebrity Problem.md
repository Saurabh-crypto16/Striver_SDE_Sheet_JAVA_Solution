```java
class Solution{ 
    //Function to find if there is a celebrity in the party or not.
    int celebrity(int M[][], int n){
    	Stack<Integer> st=new Stack<>();
    	for(int i=0;i<n;i++)    st.push(i);
    	
    	//minimum 2 people are in stack
    	while(st.size()>=2){
    	    int p1=st.pop();
    	    int p2=st.pop();
    	    
    	    //if p1 knows p2 then p1 cant be celebrity 
    	    //because celebrity does not know anyone
    	    if(M[p1][p2]==1){
    	        st.push(p2);
    	    }
    	    //if p1 does not know p2 then p2 cant be celebrity
    	    //because everyone knows celebrity 
    	    else{
    	        st.push(p1);
    	    }
    	}
    	
    	int expected_celebrity=st.pop();
    	//check entire row and col of potential celebrity
    	
    	for(int i=0;i<M.length;i++){
    	    if(i!=expected_celebrity){
    	        if(M[i][expected_celebrity]==0 || M[expected_celebrity][i]==1){
    	            return -1;
    	        }
    	    }
    	}
    	
    	return expected_celebrity;
    }
}
```
