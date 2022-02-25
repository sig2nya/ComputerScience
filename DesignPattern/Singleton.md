```java
// 하나의 객체는 단 하나의 책임만 가지며, 단 한번만 생성된다. Spring IoC는 기본적으로 Singleton Pattern을 제공한다.
public class ExampleClass {
    //Instance
    private static ExampleClass instance = new ExampleClass();

    //private construct
    private ExampleClass() {}

    public static ExampleClass getInstance() {
        return instance;
    }
}
```
