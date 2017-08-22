# spring_root
spirng study history

#### 1.2
###### 리팩토링 _refactoring_
```
기존의 코드를 외부의 동작방식에는 변화 없이 내부 구조를 변경해서 재구성하는 작업 또는 기술
예를 들어, mysql에서 postgre로 변경하였을 때 driver변경 작업을 하려면
소스 1줄을 바꿀 수도 있고 2,000줄을 바꿀 수도 있다.
유지보수 용이하게 작업하기 위한 작업

리팩토링에 관해 책 추천 『리팩토링』(마틴 파울러, 켄트 벡 공저)
```

###### 템플릿 메소드 패턴 _template method pattern_
```
슈퍼클래스에 기본적인 로직의 흐름(connection 가져오기, SQL 생성, 실행, close)을 만들고,
그 기능의 일부를 추상 메소드나 오버라이딩이 가능한 protected 메소드 등으로 만든 뒤
서브클래스에서 이런 메소드를 필요에 맞게 구현해서 사용하도록 하는 방법
```

###### 팩토리 메소드 패턴 _factory method pattern_
```
서브클래스에서 구체적인 오브젝트 생성 방법을 결정하게 하는 것
```
```java
public abstract class factoryDAO {
    public abstract Connection getConnection() throws ClassNotFoundException, SQLException;
}
.
.
.
public class AFactoryDAO extends factoryDAO {
    public Connection getConnection() throws ClassNotFoundException, SQLException {
      // sql 연결 코드
    }
}
```

**java는 클래스의 다중상속을 허용하지 않는다**

```mermaid
graph LR
UserDaoTest-->UserDao
UserDao-->ConnectionMaker
DconnectionMaker-->ConnectionMaker
UserDaoTest-->DconnectionMaker
```

**개방 폐쇄 원칙** _OCP, Open-Closed Principle_
> '클래스나 모듈은 확장에는 열려 있어야 하고 변경에는 닫혀 있어야 한다.'



#### 객체지향 설계 원칙(SOLID)
~~~
SRP(The Single Responsibility Principle) : 단일 책임 원칙
OCP(The Open Closed Principle) : 개방 폐쇄 원칙
LSP(The Liskov Substitution Principle) : 리스코프 치환 원칙
ISP(The Interface Segregation Principle) : 인터페이스 분리 원칙
DIP(The Dependency Inversion Principle) : 의존관계 역전 원칙
~~~

###### SRP
- 높은 응집도
 : 변경이 일어날 때 모듈의 많은 부분이 한꺼번에 함께 바뀐다면 응집도가 높다고 할 수 있다.
- 낮은 결합도
 : 하나의 오브젝트가 변경이 일어날 때에 관계를 맺고 있는 다른 오브젝트에게 변화를 요구하는 정도

* 서블릿(Servlet)은 자바 엔터프라이즈 기술의 가장 기본이 되는 서비스 오브젝트라고 할 숭 ㅣㅆ따.
스펙에선 강제하진 않지만, 서블릿은 대부분 **멀티스레드 환경에서 싱글톤으로 동작**한다.
이렇게 애플리케이션 안에 제한된 수, 대개 한 개의 오브젝트만 만들어서 사용하는 것이 __싱글톤__패턴의 원리다.
