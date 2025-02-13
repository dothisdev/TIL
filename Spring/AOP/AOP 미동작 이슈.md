스프링에서 AOP는 프록시를 기반으로 동작한다.
프록시 기반 AOP는 위임객체와, 메소드 위임을 사용하여 부가로직과 메인로직을 분리시킨다.
즉 원본 객체의 메인로직 코드는 유지하면서 프록시에 부가로직을 담아 역할을 분리시킨다.

프록시 기반 AOP를 사용할때 다음과 같은 상황일때 미동작 이슈가 발생한다.
1. 내부 호출
```java
public class SimpleServiceImpl implements SimpleService{
	public void outerMethod() {
		innerMethod();
	} 
	@Transactional
	public void innerMethod() {
	}
}
```
프록시 객체를 통해 outerMethod()를 호출하였을때 내부 호출된 AOP 포인트 컷 대상인 innerMethod()는 @Transactional이 적용되지 않는다.
why) @Trasactional은 프록시를 통해 적용된다. 하지만 outerMethod() 내부에 호출되는 innerMethod()는 실재객체를 통해 호출되기 때문에 즉 프록시를 통한 호출이 아니기 때문에 적용되지 않는다.

2. Private 접근자 호출
```java
public class SimpleServiceImpl implements SimpleService{
	@Transactional
	private void method() {
	}
}
```
private 접근자는 외부에서의 메소드 호출을 허용하지 않는다, 따라서 프록시라는 외부 객체를 통해 호출하는것을 허용하지 않기때문에 AOP가 적용되지 않는다.