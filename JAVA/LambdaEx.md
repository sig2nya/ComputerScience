Lambda Expressions
==================
* 정의 : 함수를 하나의 식으로 표현한 것. 함수를 람다식으로 표현하면, '메소드명'이 필요 없기 때문에 가독성이 더 좋아진다고 한다. 그렇기 때문에, '익명함수'라고도 한다.
```java
// 예를 들어...
public String hello(){
  return "Hello!"
}

// toLambda
() -> "Hello!";

/*
 * 여러 특징들
 */
 
() -> {}
() -> 1
() -> { return 1; }
 
(int x) -> x + 1;
(x) -> x + 1;
x -> x + 1;
(int x) -> { return x + 1; }
x -> { return x + 1; }

(int x, int y) -> x + y;
(x, y) -> x + y;
(x, y) -> { return x + y; }
```
