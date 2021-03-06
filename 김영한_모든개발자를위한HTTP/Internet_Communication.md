인터넷
====
<img width="1262" alt="스크린샷 2022-03-13 17 20 41" src="https://user-images.githubusercontent.com/70207093/158051284-7412fadc-f2b3-4011-be1d-dd6f753a35f5.png">

IP
==
<img width="1262" alt="스크린샷 2022-03-13 17 21 22" src="https://user-images.githubusercontent.com/70207093/158051306-fac84fe4-08af-4f76-82df-7fa018bb0cf7.png">

* Internet 통신을 위한 프로토콜
* 역할 : 지정한 IP주소에 데이터 전달, Packet 단위로 데이터를 전달한다.
* 한계 : 비연결성, 비신뢰성, 패킷 소실, 패킷 전달 순서 문제, 같은 IP를 이용하는 둘 이상의 애플리케이션 구분 불가 등의 문제가 존재한다.

TCP
===
* 특징 : 연결지향(3 way handshake), 데이터 전달 보증, 순서 보장, 신뢰성, 현재는 대부분이 TCP를 이용한다.

<img width="205" alt="스크린샷 2022-03-13 17 34 55" src="https://user-images.githubusercontent.com/70207093/158051676-c8bd4cb6-ef04-4d71-a678-d611341d23a2.png">

UDP
===
* 특징 : TCP와 정반대의 특징, 하지만 전송 속도가 빠르다. 하얀 도화지에 비유(개발자가 입맛대로 애플리케이션 레이어에서 Custome 가능)

PORT
====
* 하나의 IP에 여러 통신을 연결해야 한다면?(ex. 음악 / 방송 / 게임 등등 어느 애플리케이션으로 오는 패킷인지 구분해야한다) -> 이 때, 이용하는 것이 PORT이다.
* 같은 IP내에서 포트를 구분.

<img width="1011" alt="스크린샷 2022-03-13 17 44 50" src="https://user-images.githubusercontent.com/70207093/158051973-0741781a-775f-440a-824d-8a54bcc277c2.png">

DNS
===
* IP는 기억하기 어렵다. 또한, 요청 IP가 바뀌는 경우도 있다.(접근이 힘들어진다)
* Domain Name Service : Client가 DNS서버에 도메인 네임을 제공하면, DNS서버는 해당 도메인에 맞는 IP를 제공해준다. Client는 해당 IP를 통해 서비스에 접근 가능하다.
