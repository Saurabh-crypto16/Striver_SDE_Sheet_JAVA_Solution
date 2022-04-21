```java
/*
nth root of m will be between 1 and m
so let hi=m and lo=1
find mid of hi and lo and if mid^n > m then lo same hi=mid else lo=mid and hi same
*/

public class Solution {
    public static double findNthRootOfM(int n, long m) {
    	double l=0,r=m+1,esp=1e-8;
		
		while((r-l)>esp){
			double mid=(l+r)/2.00;
			if(multiply(mid,n) < (double)m){
				l=mid;
			}
			else{
				r=mid;
			}
		}
		
		return l;
    }
	static double multiply(double m,int n){
		double ans=1.00;
		while(n>0){
			ans*=m;
			n--;
		}
		return ans;
	}
}
```
