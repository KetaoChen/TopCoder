```java
public class CheatingAfterTests {
	public int cheat(int[] report) {
		int sum = 0;
		int diff = 0;
		for (int num : report) {
			sum += num;
			if (num < 10) {
				diff = Math.max(diff, 9 - num);
			}
			//important to check, 2 digits number also change the last digit.
			else {
				diff = Math.max(diff, Math.max(90 + num % 10 - num, 9 - num % 10));
			}
		}
		return sum + diff;
	}
}
```