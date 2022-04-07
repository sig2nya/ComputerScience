<h6>SIP에 대한 표준 규격은 RFC3261 웹 문서 참조</h6>

SIP(Session Initiation Protocol)
================================
* 정의 : Session Initiation Protocol
* VoIP 또는 멀티미디어 통신용 신호 프로토콜. 하나 이상의 양방향 멀티미디어 세션/Call을 설정, 변경, 해제를 할 수 있음
* * 세션 : 

SIP/2.0 200 OK</br>
Via: SIP/2.0/UDP server10.biloxi.com;branch=z9hG4bKnashds8;received=192.0.2.3</br>
Via: SIP/2.0/UDP bigbox3.site3.atlanta.com;branch=z9hG4bK77ef4c2312983.1;received=192.0.2.2</br>
Via: SIP/2.0/UDP pc33.atlanta.com;branch=z9hG4bK776asdhds ;received=192.0.2.1</br>
To: Bob <sip:bob@biloxi.com>;tag=a6c85cf</br>
From: Alice <sip:alice@atlanta.com>;tag=1928301774</br>
Call-ID: a84b4c76e66710@pc33.atlanta.com</br>
CSeq: 314159 INVITE</br>
Contact: <sip:bob@192.0.2.4></br>
Content-Type: application/sdp</br>
Content-Length: 131</br>

```js
                     atlanta.com  . . . biloxi.com
                 .      proxy              proxy     .
               .                                       .
       Alice's  . . . . . . . . . . . . . . . . . . . .  Bob's
      softphone                                        SIP Phone
         |                |                |                |
         |    INVITE F1   |                |                |
         |--------------->|    INVITE F2   |                |
         |  100 Trying F3 |--------------->|    INVITE F4   |
         |<---------------|  100 Trying F5 |--------------->|
         |                |<-------------- | 180 Ringing F6 |
         |                | 180 Ringing F7 |<---------------|
         | 180 Ringing F8 |<---------------|     200 OK F9  |
         |<---------------|    200 OK F10  |<---------------|
         |    200 OK F11  |<---------------|                |
         |<---------------|                |                |
         |                       ACK F12                    |
         |------------------------------------------------->|
         |                   Media Session                  |
         |<================================================>|
         |                       BYE F13                    |
         |<-------------------------------------------------|
         |                     200 OK F14                   |
         |------------------------------------------------->|
         |                                                  |
```

Response Status Code
====================
```js
      1xx: Provisional -- request received, continuing to process the
           request;

      2xx: Success -- the action was successfully received, understood,
           and accepted;

      3xx: Redirection -- further action needs to be taken in order to
           complete the request;

      4xx: Client Error -- the request contains bad syntax or cannot be
           fulfilled at this server;

      5xx: Server Error -- the server failed to fulfill an apparently
           valid request;

      6xx: Global Failure -- the request cannot be fulfilled at any
           server.
```

SIP의 구성 요소
===============
1. UA(User Agent) : UAC와 UAS를 동시에 포함하는 논리적 구조
2. UAC(User Agent Client) : Request 메시지를 생성하여 전송하는 논리적 구성 요소
3. UAS(User Agent Server) : Request를 처리하고, Response 메시지를 반환하는 논리적 구성 요소
4. End-Device
* * SIP Phone
* * PC/Laptop with SIP Client
* * PDA
* * Mobile Phone

User Agent
==========
* B2BUA(Back-To-Back User Agent)
* * Request 메시지를 수신하고, 이를 처리하기 위해 UAS로 동작
* * Response 메시지를 생성하기위해 UAC로 동작하여 새로운 Request 메시지를 외부로 전송
* * Proxy Server의 동작 형태 중 하나
* * 모든 Call 처리 상태 정보를 유지 관리
