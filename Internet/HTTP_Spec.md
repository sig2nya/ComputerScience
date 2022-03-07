HTTP
====
* 정의 : HyperText Transfer Protocol. HTML문서를 교환하기 위한 통신 상호 규약.
* HTTP 메시지 기본 구조</br>
![image](https://user-images.githubusercontent.com/70207093/156974092-f69a075d-9bdc-40f3-9d31-c5838f532021.png)
* * Start Line : Request / Response에 따라 다르다. 
* * Header : 'Key:Value'로 구성되어 있다. HTTP 전송에 필요한 모든 부가 정보를 갖고 있다.
* * Body : 메시지의 본문을 담는다.

HTTP 특징
========
* Stateless : 이전 요청과 다음 요청이 관계가 없다. 서버는 클라이언트를 식별할 수 없다. 이를 통하여, 서버의 부하를 줄여준다.
* Conectionless : 요청/응답이 완료되면, 연결을 끊는다. 이를 통한 단점이 생기는데, 서버는 클라이언트를 기억하지 않으니 매번 연결/해제 과정이 일어난다.

Cookie
======
* HTTP의 Stateless 문제 해결을 위하여 Cookie를 이용할 수 있다.
* Cookie는 Server측에서 Response Header에 포함하여 Web Browser에 심는다.
* Cookie는 보안에 취약하다.(위/변조가 쉽다)
* * 쿠키의 구성 요소 : 이름, 값, 유효시간, 도메인, 경로

Session
=======
* Cookie와 다르게, Session은 사용자에 대한 정보를 Server측에서 사용자 정보를 저장한다.
* 일반적으로, 쿠키보다 보안에 뛰어나다.
* Server측에서 정보를 갖고 있으니, Server 성능 저하의 원인이 된다.
* * Session 생성 과정 : Client는 Server에 접속 -> Server는 Session ID 발급 -> Client는 Session ID에 대한 Cookie 생성 -> Client가 Server에 재요청시, Cookie를 이용하여 Session 발급
* * 특징 : 각 Client에 고유 ID, Cookie보다 높은 보안성, 사용자 증가시 Server측 메모리 증가.

HTTP Structure
==============
<img width="556" alt="스크린샷 2022-03-05 14 41 01" src="https://user-images.githubusercontent.com/70207093/156869944-8dfbe4a3-3403-4f87-8503-d239af94063b.png">


[HTTP Request]</br>
GET /hello?username = world HTTP/1.1</br>
HOST: localhost:8080</br>
</br>
[HTTP Response]</br>
HTTP/1.1 200 OK</br>
Content-Type: text/plain; charset = UTF-8 Content-Length: 11</br>
Hello, World!</br>

start-line 정보 Spring에서 확인하기
-------------
```java
    private void printStartLine(HttpServletRequest request) {
        System.out.println("--- REQUEST-LINE - start ---");
        System.out.println("request.getMethod() = " + request.getMethod()); //GET
        System.out.println("request.getProtocal() = " + request.getProtocol()); //HTTP/1.1
        System.out.println("request.getScheme() = " + request.getScheme()); //http
        // http://localhost:8080/request-header
        System.out.println("request.getRequestURL() = " + request.getRequestURL());
        // /request-test
        System.out.println("request.getRequestURI() = " + request.getRequestURI());
        //username=hi
        System.out.println("request.getQueryString() = " + request.getQueryString());
        System.out.println("request.isSecure() = " + request.isSecure()); //https 사용 유무
        System.out.println("--- REQUEST-LINE - end ---");
        System.out.println();
    }
```
Console Result
--------------
```
--- REQUEST-LINE - start ---
request.getMethod() = GET
request.getProtocal() = HTTP/1.1
request.getScheme() = http
request.getRequestURL() = http://localhost:8080/request-header
request.getRequestURI() = /request-header
request.getQueryString() = username=hello
request.isSecure() = false
--- REQUEST-LINE - end ---
```
헤더 정보 Spring에서 확인하기
----------------
```java
    private void printHeader(HttpServletRequest request){
        System.out.println("--- Headers - start ---");
        Enumeration<String> headerNames = request.getHeaderNames();
        while(headerNames.hasMoreElements()){
            String headerName = headerNames.nextElement();
            System.out.println(headerName + " : " + headerName);
        }
        System.out.println("--- Headers - end ---");
        System.out.println();
    }
```
Console Result
--------------
```
--- Headers - start ---
host : host
connection : connection
cache-control : cache-control
sec-ch-ua : sec-ch-ua
sec-ch-ua-mobile : sec-ch-ua-mobile
sec-ch-ua-platform : sec-ch-ua-platform
upgrade-insecure-requests : upgrade-insecure-requests
user-agent : user-agent
accept : accept
sec-fetch-site : sec-fetch-site
sec-fetch-mode : sec-fetch-mode
sec-fetch-user : sec-fetch-user
sec-fetch-dest : sec-fetch-dest
accept-encoding : accept-encoding
accept-language : accept-language
cookie : cookie
--- Headers - end ---
```
Header 편리한 조회 Spring에서 확인하기
----------------
```java
    private void printHeaderUtils(HttpServletRequest request) {
        System.out.println("--- Header 편의 조회 start ---");
        System.out.println("[Host 편의 조회]");
        System.out.println("request.getServerName() = " +
                request.getServerName()); //Host 헤더
        System.out.println("request.getServerPort() = " +
                request.getServerPort()); //Host 헤더
        System.out.println();
        System.out.println("[Accept-Language 편의 조회]");
        request.getLocales().asIterator()
                .forEachRemaining(locale -> System.out.println("locale = " +
                        locale));
        System.out.println("request.getLocale() = " + request.getLocale());
        System.out.println();
        System.out.println("[cookie 편의 조회]");
        if (request.getCookies() != null) {
            for (Cookie cookie : request.getCookies()) {
                System.out.println(cookie.getName() + ": " + cookie.getValue());
            }
        }
        System.out.println();
        System.out.println("[Content 편의 조회]");
        System.out.println("request.getContentType() = " +
                request.getContentType());
        System.out.println("request.getContentLength() = " +
                request.getContentLength());
        System.out.println("request.getCharacterEncoding() = " +
                request.getCharacterEncoding());
        System.out.println("--- Header 편의 조회 end ---");
        System.out.println();
    }
```
Console Result
--------------
```
--- Header 편의 조회 start ---
[Host 편의 조회]
request.getServerName() = localhost
request.getServerPort() = 8080

[Accept-Language 편의 조회]
locale = ko_KR
locale = ko
locale = en_US
locale = en
request.getLocale() = ko_KR

[cookie 편의 조회]
JSESSIONID: 27280C9D2C968F28C4A4A58EBA56CD56

[Content 편의 조회]
request.getContentType() = null
request.getContentLength() = -1
request.getCharacterEncoding() = UTF-8
--- Header 편의 조회 end ---
```
