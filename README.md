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


## 2. 버전
* v0 : 로그없이 로직만 존재
* v1 : 클래스마다 로그코드 적용
* v2 : 로그남길때 동일한 프로세스 로그인지 확인을 위해  uuid 적용(동시성문제 발생)
* v3 : ThreadLocal 을 위용한 동시성문제 해결
  - ThreadLocal : Thread 마다 메모리 할당
```java
private final ThreadLocal<T> threadLocal = new ThreadLocal<>();
object = threadLocal.get();
threadLocal.set(T);
threadLocal.remove();
``` 
* v4 : 로그를 남기는 로직 중복을 제외하기 위해 추상클래스를 적용하여 중복 제외

