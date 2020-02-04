```java
import java.util.*;
import java.lang.*;

public class BlackAndWhiteBallsEasy {
	public int getNumber(int[] balls, int white, int black) {
    	//dp[i] is the number of ways to split row for first ith balls.
        //we need to find a index that makes i-j have black black balls or white white balls
        int mod = (int) (1e9 + 7);
        List<Integer> list = new ArrayList<>();
        for (int i = 0; i < balls.length; i++) {
        	for (int j = 0; j < balls[i]; j++) {
            	list.add(i % 2);    
                //0 represent white, 1 represent black.
            }
        }
        int l = list.size();

        
        long[] dp = new long[l + 1];
        dp[0] = 1;
        for (int i = 1; i <= l; i++) {
            //find the index that can make white or black have required value
            int countB = 0;
            int countW = 0;
        	for (int k = i; k > 0; k--) {
                if (list.get(k - 1) == 0) {
                	countW++;    
                }
                else {
                	countB++;    
                }
                if (countW == white) {
                    dp[i] =  (dp[i] + dp[k - 1]) % mod;
                }
                if (countB == black) {
                    dp[i] =  (dp[i] + dp[k - 1]) % mod;
                }
            }
        }
        return (int) (dp[l] % mod);
    }
}
```