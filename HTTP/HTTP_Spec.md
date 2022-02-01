HTTP Spec</br>
---------
![image](https://user-images.githubusercontent.com/70207093/151931506-ff2b0644-db1e-4a41-90ce-7de37773ea02.png)

[HTTP Request]</br>
GET /hello?username = world HTTP/1.1</br>
HOST: localhost:8080</br>
</br>
[HTTP Response]</br>
HTTP/1.1 200 OK</br>
Content-Type: text/plain; charset = UTF-8 Content-Length: 11</br>
Hello, World!</br>

Spring에서 확인하기
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
Spring에서 확인하기
----------------
```
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
Spring에서 확인하기
```
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
