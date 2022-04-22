```java
public class Solution {
    public int books(ArrayList<Integer> A, int B) {
        int totalStudents=A.size(), allowedStudents=B;
        long sum = 0;
        
        if (totalStudents < allowedStudents) return -1;
        
        for (int i: A) {
            sum += i;
        }
        
        int start = 0;
        int end = (int)sum;
        int res = Integer.MAX_VALUE;
        while(start <= end) {
            int mid = (start + end)/2;
            if (isPossible(A, totalStudents, allowedStudents, mid)) {
                res = Math.min(res, mid);
                end = mid-1;
            }
            else {
                start = mid+1;
            }
        }
        return res;
    }
    public boolean isPossible(ArrayList<Integer> A, int totalStudents, int allowedStudents, 
                            int currMin) {
        int studentsReq = 1;    //stores the count of number of students to whom book has been allocated
        int currSum = 0;
        for (int i=0; i<totalStudents; i++) {
            //if any book has move number of pages than the limit
            if (A.get(i) > currMin) {
                return false;
            }
            if (currSum + A.get(i) > currMin) {
                studentsReq++;
                currSum = A.get(i);
                //if studentes to whom books are allocated exceed limiting students 
                if (studentsReq > allowedStudents) {
                    return false;
                }
            }
            else {
                currSum += A.get(i);
            }
        }
        return true;
    }
}
```
