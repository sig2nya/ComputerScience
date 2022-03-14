웹브라우저 요청 흐름
===============
* 웹 브라우저가 https://www.google.com/search?q=hello&hl=ko 를 요청
* DNS를 조회하고, HTTP 요청 메시지가 다음과 같이 생성된다.
* HTTP 요청 메시지 생성 -> Socket 라이브러리를 통해 전달 -> TCP/IP 연결 -> TCP/IP 패킷 생성 / HTTP 메시지 포함 -> LAN Driver를 통하여 인터넷 망으로 전달 -> 서버가 응답 메시지 생성
<img width="480" align="left" alt="스크린샷 2022-03-14 12 26 32" src="https://user-images.githubusercontent.com/70207093/158099742-2f47dc34-6ad0-4b54-af6e-89a47307f8c1.png">
<img width="480" align="right" alt="스크린샷 2022-03-14 12 33 39" src="https://user-images.githubusercontent.com/70207093/158100326-63eb2c51-5987-4237-adb9-f473ee715535.png">
