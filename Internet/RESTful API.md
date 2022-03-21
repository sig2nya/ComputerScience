REST(Representational States Transfer) API
==========================================
- REST API는 웹의 장점을 최대한으로 살리기 위한 아키텍처이다.
- 구성 요소 : 자원(URI), 행위(HTTP Method), 표현
IBM : RESTful API 설명 링크 https://www.ibm.com/kr-ko/cloud/learn/rest-apis

REST API 디자인 원칙 6가지
======================
```
1. 균일한 인터페이스 : 요청이 어디서 오는지와 무관하게, 동일 URI에 대한 요청은 동일하게 보여야한다.
2. 클라이언트 - 서버 : 클라이언트와 서버 애플리케이션은 서로 완전히 독립되어야 한다. 클라이언트가 알아야 하는 유일한 요청은 URI이며, 다른 방법으로는 서버와 상호작용 할 수 없다.
3. Stateless : 각 요청에서 필요한 정보를 모두 포함시킨다. 서버측 세션이 필요하지 않다.
4. 캐싱 : 리소스를 클라이언트 / 서버 측에서 캐시가 가능해야한다. 서버측의 확장성 증가와 클라이언트의 효율성 증대를 위해서이다.
5. 계층 구조 아키텍처 : 호출과 응답이 서로 다른 계층을 통해서 전달된다. 보통, 클라이언트와 서버는 직접적으로 연결되는 것이 아니다. 다수의 중개자(프록시)가 존재할 수 있다.
```
REST API 디자인 가이드
===================
- URI는 정보의 자원을 표현해야 한다.</br>
\- GET /members/show/1     (x)</br>
\- GET /members/1          (o)</br></br>
- 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE)로 표현한다.</br>

|METHOD|역할|
|------|---|
|POST|POST를 통해 해당 URI를 요청하면 리소스를 생성합니다.|
|GET|GET를 통해 해당 리소스를 조회합니다. 리소스를 조회하고 해당 도큐먼트에 대한 자세한 정보를 가져온다.|
|PUT|PUT를 통해 해당 리소스를 수정합니다.|
|DELETE|DELETE를 통해 리소스를 삭제합니다.|

RESTful API Exam
================
```java
@RestController
public class ApiController {
    @RequestMapping(value = "/api/test", method = RequestMethod.GET)
    @ResponseStatus(value = HttpStatus.OK)
    public String getApiTest(){
        return "{\"result\":\" ok\"}"; // Json 형태로 반환
    }

    @RequestMapping(value = "/api/test2", method = RequestMethod.POST)
    @ResponseStatus(value = HttpStatus.OK)
    public String getApiTest2(){
        return "{\"result\":\" hi\"}";
    }
}
```
