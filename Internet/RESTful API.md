REST(Representational States Transfer) API
========
- REST API는 웹의 장점을 최대한으로 살리기 위한 아키텍처이다.
- 구성 요소 : 자원(URI), 행위(HTTP Method), 표현

> - 특징</br>
> URI로 지정된 자원에 대하여 조작을 통일되고 한정적인 인터페이스를 수행하는 아키텍처</br>
> 무상태성을 통해 상태정보를 저장하지 않는다. 세션정보나 쿠키를 따로 저장하지 않음</br>
> HTTP의 성격을 갖기 때문에 캐싱이 가능하다. (캐싱 : 애플리케이션의 수행 속도를 빠르게 해준다. 정적인 파일들을 특정 위치에 저장하여, 요청이 왔을 때 빠르게 응답이 가능하다)</br>
> REST API의 메시지만 보고도 요청 내용을 유추 가능하다.

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
