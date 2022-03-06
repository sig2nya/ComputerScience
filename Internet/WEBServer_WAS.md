* 참고해보면 좋을 사이트 : https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html </br>

WEB Server
==========
* 기능 : WEB Server는 주로 <b>Static Resource</b>를 제공하기 위해 사용한다.
* * 정적 리소스(Static Resource) : HTML, CSS, Image, JS 등등...
* WEB Server : HW + SW / HW에는 웹 서버가 설치되어 있으며, SW는 정적 리소스를 제공하는 애플리케이션이다.
* * 기능 : HTTP 기반으로 Client의 요청을 처리하여 그에 맞는 응답을 반환한다. 이 때, 반환하는 자원이 정적 리소스이다. WAS를 거치지 않고 제공되므로, WAS의 부하를 줄여준다.</br>
\* 만약, 동적 리소스 요청이 들어온다면 WEB Server에서는 이를 확인하여 WAS에 요청한다.
* 종류 : NginX, Apache Server, IIS 등</br>
![image](https://user-images.githubusercontent.com/70207093/156868339-b55aecad-d370-439c-b612-07cc139b9413.png)

WEB Application Server(WAS)
===========================
* 기능 : WAS는 <b>Dynamic Resource</b>를 제공하기 위해 사용한다.
* * 동적 리소스(Dynamic Resource) : JSP, Servlet 등등...
* WEB Application Server : WEB Server + Container / WAS는 기본적으로 WEB Server의 기능도 갖는다. WEB Server와 따로 구분하는 이유는 WAS의 부담을 덜어주기 위해서이다.
* * Container : JSP / Servlet을 실행시킬 수 있는 환경이다.
* 종류 : Apache Tomcat, JBoss, Jeus 등</br>
![image](https://user-images.githubusercontent.com/70207093/156868629-82c3bd28-6fa1-428f-b2c7-69c9b6733ecc.png)
</br>

* WEB Service Architecture는 다양한 구조를 가질 수 있다.
* * Client -> WEB Server -> DB
* * Client -> WEB Application Server -> DB
* * Client -> WEB Server -> WEB Application Server -> DB

WAS가 Dynamic Resource 요청을 처리하는 과정
=====================================
* Client Request -> (WEB Server) -> WAS가 요청 확인 -> 해당 요청에 맞는 Servlet(Service) 호출(GET / POST) -> 동적 페이지 생성 및 WAS에 전달 -> WAS가 Client에 페이지를 반환

Apache Tomcat 동작 원리
=====================
* Client Request -> Servlet Container가 Request / Response 객체 생성 -> WAS가 요청 URL 분석 -> URL에 맞는 Servlet / Service 호출 -> HTTP Method에 따라, doGet / doPost 메서드 호출 -> 요청이 완료되면 Response에 응답 -> 응답 후, Request / Response 객체 소멸 -> Shutdown(Socket을 닫음)

Apache Tomcat Directory Structure
=================================
![image](https://user-images.githubusercontent.com/70207093/156909353-d60f7559-5233-40ea-b63e-f3c4f65eca34.png)

|Name   |Discription|
|-------|-----------|
|bin    |톰캣 구동을 위한 Script file(.sh, .bat)|
|conf   |Configuration 설정 파일              |
|lib    |톰캣 구동을 위한 lib(jar) 파일          |
|logs   |예외 발생 사항 등에 대한 로그             |
|temp   |임시 저장용 폴더                       |
|webapps|웹 애플리케이션 파일                    |
|work   |Servlet으로 변환된 java / class 파일   |
