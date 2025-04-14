```java
import java.util.Scanner;

public class Main{
	public static void main(String[] args){
		// 일반적인 스캐너 생성
		Scanner sc = new Scanner(System.in);
		
		// 스캐너를 통해 값 입력방법
		// 스트링을 제외한 값 입력은 nextTYPE()을 호출
		sc.nextInt();
		sc.nextFloat();
		
		// 한단어만 읽음 - sc is scanner -> sc
		sc.next();
		// 한 줄을 읽음 - sc is scanner -> sc is scanner
		sc.nextLine();
	}
}
```
