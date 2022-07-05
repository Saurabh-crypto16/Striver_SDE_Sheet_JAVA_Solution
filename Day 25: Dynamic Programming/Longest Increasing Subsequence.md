```java
/*
    Time Complexity : O(N * log(N))
    Space Complexity : O(N)

    Where N is the size of the array
*/

public class Solution {
    private static int lowerBound(int[] a, int low, int high, int element) {
        while (low < high) {
            int middle = low + (high - low) / 2;
            if (element > a[middle]) {
                low = middle + 1;
            }else{
                high = middle;
            }
        }

        return low;
    }
    public static int longestIncreasingSubsequence(int arr[]) {
        int n = arr.length;
        // dp[i] represents i+1'th length LIS ending at minimum integer dp[i]
        int dp[] = new int[n];
        int ans = 0;
        for (int i = 0; i < n; i++) {
            int position = lowerBound(dp, 0, ans, arr[i]);
            dp[position] = arr[i];
            if (position == ans) {
                ans++;
            }
        }

        return ans;
    }
}
```
