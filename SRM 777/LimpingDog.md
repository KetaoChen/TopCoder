```java
public class LimpingDog{
    public int countSteps(int time) {
        int res = 0;
        while (time > 0) {
        	if (res % 4 == 2) {
            	time -= 2;    
            }
            else {
                time -= 1;
            }
            if (time < 0) {
                return res;
            }
            res++;
            if (res % 47 == 0) {
            	time -= 42;    
            }
        }
        return res;
    }
}
```