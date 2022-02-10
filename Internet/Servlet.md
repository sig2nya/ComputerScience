Servlet Container</br>
======================
: 서블릿들의 생성, 실행, 파괴를 담당한다.</br>
: 서블릿들을 위한 상자(Container)
![image](https://user-images.githubusercontent.com/70207093/153368850-a7712dd3-6707-4c0c-8ee4-33c4b84cc77d.png)

Servlet</br>
============
: client들의 요청을 처리하기 위한 JAVA Application</br>
: Servlet은 HttpServlet class를 상속받아 구현한다</br>
***
> 다음과 같은 메서드를 정의하여 사용한다.</br>
 > init() : 서블릿 생명 주기 중 초기화 단계에 호출된다.</br>
 > service() : 초기화 이후 각각의 요청들이 들어오면 호출된다.</br>
 > destroy() : 서블릿 객체가 파괴되어야 할 때 호출된다. 해당 서블릿이 갖고 있던 자원들을 반환한다.</br>

Servlet의 특징</br>
1. Client의 요청에 동적으로 작동
2. Java Thread를 이용해 동작
3. HTML 변경 시 재컴파일 필요
4. <b>Java 코드에 HTML이 들어가있음</b>
5. HTML을 사용해서 요청에 응답
