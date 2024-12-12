# ※ 인텔리제이 유용한 단축키 
* 변수생성 : Ctrl + Alt + v
* 리펙토리(항수명 추가) : Alt + Enter
* 테스트클래스 생성 : Ctrl + Shift + t

# 스프링 핵심 원리 - 고급편
## 1. 로그생성 요구사항
* 모든 PUBLIC 메서드의 호출과 응답 정보를 로그로 출력
* 애플리케이션의 흐름을 변경하면 안됨
* 로그를 남긴다고 해서 비즈니스 로직의 동작에 영향을 주면 안됨
* 메서드 호출에 걸린 시간
* 정상 흐름과 예외 흐름 구분
* 예외 발생시 예외 정보가 남아야 함
* 메서드 호출의 깊이 표현
* HTTP 요청을 구분
* 정상 요청
  - HTTP 요청 단위로 특정 ID를 남겨서 어떤 HTTP 요청에서 시작된 것인지 명확하게 구분이 가능해야 함
  - 트랜잭션 ID 여기서는 하나의 HTTP 요청이 시작해서 끝날 때 까지를 하나의 트랜잭션이 라 함


## 2. 동시성문제 해결
* ThreadLocal 사용
```java
private final ThreadLocal<T> threadLocal = new ThreadLocal<>();

object = threadLocal.get();
threadLocal.set(object);
threadLocal.remove();
```

