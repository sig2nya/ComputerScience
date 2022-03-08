OSI 7 Layers
===========
<h3>OSI란?</h3>

* Open System Interconnection Reference Model(OSI) 의 약자로 직역하자면 '개방 시스템 상호연결 참조 모델'이라고 해석할 수 있다.
* 통신에 대해 계층화 시킨 모델이다.
* 국제 표준화기구 ISO에서 개발하였다.
<p align="center">
  <img width="578" alt="스크린샷 2022-03-02 19 10 15" src="https://user-images.githubusercontent.com/70207093/156341276-a3ff91fc-55ee-4e66-bea0-0f4495b4368b.png"/>
</p>

계층의 종류
========
|저수준|<------|-----|-----|-----|----->|고수준|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|물리|데이터링크|네트워크|전송|세션|표현|응용|

<b>* 정처기 공부할 때, '물데네전세표응'이라고 외웠다.(필자는 21년 하반기 모 공기업 면접에서 OSI 7계층에 관한 질문을 받았었다.)</b>

물리계층
======
* 물리계층은 통신이 성립하기 위한 연결을 물리적으로 수행한다. 즉, 송신기와 수신기가 유선/무선 통신이 가능하도록 연결을 확립해주는 계층이다.
* 컴퓨터는 1과 0의 신호만 이해할 수 있다. 유선통신이라면, 전기적 Signal을 전송하면 1, 그렇지 않다면 0에 대응 될 것이며, 무선통신이라면 진폭 변조 혹은 파수 변조에 의해 1과 0을 구분할 수 있게끔 한다.
* 유선의 경우 예를 들자면, 송신기가 전달하는 전기적 신호의 전압 세기를 수신기는 이해해야 할 것이며, 이를 위해 상호 협약이 이루어져야 할 것이다.
* 무선의 경우 예를 들어, 송신기에서 전달하는 전자기파의 변조는 어떻게 이루어지는지 수신기는 이해해야 할 것이며, 수신기는 그에 맞는 변환을 통해 송신기의 데이터를 이해해야 할 것이다.
* 물리계층은 데이터 전달에만 관심이 있다. 즉, 신호를 전달하는 것만 관심이 있다.
* 단위는 당연하게도 Bit이다.
(차후, 디지털 변조에 대한 내용도 다루어야겠다.)

* 대표장비 : 허브 / 리피터</br>
![image](https://user-images.githubusercontent.com/70207093/156887679-26f0f207-51c7-4c35-b2b9-0ed8345f19cf.png)

데이터 링크 계층
============
* 인접한 노드들끼리 데이터를 전송하고 물리계층에서의 오류를 감지하는 역할이다.
* 프레임을 생성하고, 흐름 / 오류 제어 수행, 회선 제어도 수행한다.
* * 회선 제어 : ENQ/ACK 기법, Polling 기법
* * ENQ/ACK : Enquery / Acknowledge, 송신측이 Enquery 수신측이 Acknowledge, 1:1 전송 기법
* * Polling : Select모드를 통하여 송신측이 전송할 수신측을 선택한다. 1:多 전송 기법
* 데이터 단위는 Frame, 대표 프로토콜은 Ethernet, Tocken Ring, FDDI 사용</br>
![image](https://user-images.githubusercontent.com/70207093/157163951-5ba1ea68-b512-465e-9541-cddd46f9f09c.png)

네트워크 계층
==========
* 경로제어를 수행한다. 발신에서 착신까지의 패킷을 제어한다. 대표적으로, 라우팅이 있다.
* 대표 프로토콜 : IP, IPsec, ICMP(Internet Control Message Protocol), IGMP(Internet Group Management Protocol) *정보처리기사에서 많이 나오는 문제였음.
* * IP(Internet Protocol) : 인터넷을 이용하기 위한 프로토콜. 비신뢰성, 비연결성 프로토콜. 즉, 보낸 정보가 수신이 제대로 이루어졌는지 확인하지 않는다. 순서도 뒤죽박죽이 될 수 있다. 이 문제를 해결하기 위해서는 TCP를 이용한다.
* * IPsec : IP에 Security를 추가한 기능. 자세한 내용은 따로 다루어보자.
* * ICMP(Internet Control Message Protocol) : IP Packet을 처리할 때, 발생되는 문제를 알리기 위한 프로토콜이다. Ping 명령어 같은 경우에도 ICMP를 이용한 기능이라고 볼 수 있다. ICMP를 통해 DDoS 공격이 이루어질 수도 있다.
* * IGMP(Internet Group Management Protocol) : Subnet간의 멀티캐스트를 위한 프로토콜로 사용된다. 주로 IPTV 외에서는 잘 사용되지 않는다.
* 데이터 단위는 Packet

*JAVA Socket 통신 기회가 있으면 해보자.(https://mainpower4309.tistory.com/25)
```java
// Server측 
package network;

import java.io.DataOutputStream;
import java.io.IOException;
import java.io.OutputStream;
import java.net.ServerSocket;
import java.net.Socket;

public class DemoServer {
    public static void main(String[] args) throws IOException {
        int port = 5050;
        int number = Integer.parseInt(args[0]);
        String str = new String(args[1]);
        ServerSocket ssk = new ServerSocket(port); // ServerSocket 설정

        System.out.println("접속 대기중...");


        while(true){
            Socket socket = ssk.accept();
            System.out.println("사용자 접속 완료.");
            System.out.println("Client IP : " + socket.getInetAddress());

            OutputStream ous = socket.getOutputStream();
            DataOutputStream dous = new DataOutputStream(ous);

            dous.writeUTF(str);
            dous.writeInt(number);
            dous.flush();
            dous.close();
            socket.close();
        }
    }
}

```
```java
// Client 측
package network;

import java.io.DataInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.net.ConnectException;
import java.net.Socket;

public class Client {
    public static void main(String[] args) throws IOException {
        try{
            Socket socket = new Socket("127.0.0.1", 5050);
            System.out.println("서버와 접속이 되었습니다.");

            InputStream ins = socket.getInputStream();
            DataInputStream dins = new DataInputStream(ins);
            String str= dins.readUTF();
            int number = dins.readInt(); // 정수형형태로 데이터를 읽어오기 위한 메소드
            System.out.println("서버에서 전송된 값 : " + number  );
            System.out.println("서버에서 전송된 문자 : " + str  );

            dins.close();
            ins.close();
            socket.close();
        } catch(ConnectException e){
            System.out.println("연걸이 거절되었습니다.");
        }
    }
}


```
* 결과물</br>
<img width="1138" alt="스크린샷 2022-03-08 15 05 33" src="https://user-images.githubusercontent.com/70207093/157176832-0fc61b5e-f906-4925-9315-b4af311b81f4.png">

전송 계층
=======
* 목적지에 신뢰성 있는 데이터 전송을 위한 계층이다. 오류 점검과 목적지의 애플리케이션을 식별하는 역할이다.
* 신뢰/효율성 있는 데이터 전송을 보장한다.(1,2,3계층만 존재하여도 데이터 전송이 가능하다. 하지만, 신뢰성 있는 데이터 전송을 보장하지는 않는다)
* * 연결형 통신(TCP) : 1) 데이터를 보내도 되나요? 2) 네, 보내도 됩니다. 3) 보냅니다! 4) 받았습니다 5) 확인했습니다.
* * 비연결형 통신(UDP) : 데이터를 보냅니다. END...
> TCP(Transmission Control Protocol) : 연결 지향형 프로토콜. 신뢰성있는 데이터를 제공한다. 전송 순서가 보장된다.
> * 실시간 전송에 불리하다.(ex. Streaming Service)
> > * 3-Way-HandShaking(통신 시작) : Client가 SYN 패킷 전송 / 응답 대기 -> Server는 SYN+ACK 패킷을 Client로 응답 -> Client는 ACK패킷을 다시 보내 통신 시작.</br>
> > * 4-Way-HandShaking(통신 종료) : Client가 FIN 패킷 전송 / 응답 대기 -> Server는 Time-Wait상태로 통신이 끝날 때까지 대기 -> 통신이 종료되면 Server가 Client에게 FIN 패킷 전송 -> Client는 확인 응답 전송

> UDT(User Datagram Protocol) : 비연결 지향형 프로토콜. 신뢰성있는 데이터 전송에 부적합하다. 서로 다른 경로로 패킷을 전송한다(순서 보장 안됌).
