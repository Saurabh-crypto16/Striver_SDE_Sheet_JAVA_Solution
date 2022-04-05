```java
//Solution 1 Using XOR

/*
Brute: Hashing of elements in an array
Better: Let x=missing no and y=repeated no S=(n*(n+1)/2) and S=(n*(n+1)*(2n+1)/6)
        so x-y=S and x^2-y^2=S^2 using these 2 find x and y
Best: use xor so (xor of array) xor (xor from 1 to n) will give x^y where x is missing no and  y is repeated no. 
      Seperate the nums of A in 2 baskets based on the right most set bit in x^y and do the same for numbers from (1 to n) in same baskets 
      then xor the buckets and that will be answer   
*/
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public ArrayList<Integer> repeatedNumber(final List<Integer> A) {
        /* Will hold xor of all elements
        and numbers from 1 to n  */
        int xor1,n=A.size();
 
        /* Will have only single set bit of xor1 */
        int set_bit_no;
 
        int i;
        int x = 0;
        int y = 0;
 
        xor1 = A.get(0);
 
        /* Get the xor of all array elements  */
        for (i = 1; i < n; i++)
            xor1 = xor1 ^ A.get(i);
 
        /* XOR the previous result with numbers from 1 to n*/
        for (i = 1; i <= n; i++)
            xor1 = xor1 ^ i;
 
        /* Get the rightmost set bit in set_bit_no */
        set_bit_no = xor1 & ~(xor1 - 1);
 
        /* Now divide elements into two sets by comparing rightmost set bit of xor1 with the bit at the same position in each element. 
        Also, get XORs of two sets. The two XORs are the output elements. The following two for loops serve the purpose */
        for (i = 0; i < n; i++) {
            if ((A.get(i) & set_bit_no) != 0)
                /* arr[i] belongs to first set */
                x = x ^ A.get(i);
 
            else
                /* arr[i] belongs to second set*/
                y = y ^ A.get(i);
        }
        for (i = 1; i <= n; i++) {
            if ((i & set_bit_no) != 0)
                /* i belongs to first set */
                x = x ^ i;
 
            else
                /* i belongs to second set*/
                y = y ^ i;
        }

        ArrayList<Integer> ans=new ArrayList<>();
        ans.add(x);
        ans.add(y);
        return ans;
    }
}


//Solution 2 
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public ArrayList<Integer> repeatedNumber(final List<Integer> A) {
        
        
        ArrayList<Integer> out = new ArrayList<Integer>();
        double l = A.size();
        double sum = (l*(l+1))/2;
        long sumA = 0;
        int a=0;
        HashSet<Integer> ASet = new HashSet<Integer>();
        for(int i=0;i<A.size();i++) {
            if(ASet.contains(A.get(i))) {
                a=A.get(i);
            }
            ASet.add(A.get(i));
            sumA = sumA+A.get(i);
        }
        double diff = sumA - sum;
        int b = a - (int)diff;
        out.add(a);
        out.add(b);
        return out;
    
    
    }
}
