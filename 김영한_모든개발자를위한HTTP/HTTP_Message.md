HTTP Message 구조
================
<img width="561" alt="스크린샷 2022-03-14 13 07 09" src="https://user-images.githubusercontent.com/70207093/158103213-cfa2917e-4ff0-4900-be20-aac34c4c16bd.png">

* Start Line
* * Request Line : Method Request-Target HTTP-Version
* * HTTP Method : GET, POST, PUT, DELETE ...
* * Request-Target : absolute-path[?query] + HTTP-Version
* Header
* * HTTP 전송에 필요한 모든 정보 : 메시지 바디, 크기, 압축, 인증, 요청 브라우저, 서버 애플리케이션 정보, 캐시 관리 정보.
* HTTP Message Body
* * HTML, Image, 동영상, JSON 등등 모든 데이터 전송 가능.
