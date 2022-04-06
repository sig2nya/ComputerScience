*SIP에 대한 표준 규격은 RFC3261 웹 문서 참조

SIP(Session Initiation Protocol)
================================
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
