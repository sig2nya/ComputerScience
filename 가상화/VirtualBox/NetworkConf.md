* 참고 : https://technote.kr/213

Virtual Box Network Configuration
=================================
* 개요 : Virtual Box로 가상화를 구성하는데 Host를 통한 네트워크 접근, VM 자체로부터 네트워크 접근 등 좀 더 세부적으로 네트워크 설정 방법을 공부하고자 작성.(공부할게 왜이리 많은지...)
* 다음과 같이 Virtual Box의 네트워크 환경 설정을 보자</br>
  <img width="501" alt="image" src="https://user-images.githubusercontent.com/70207093/178914931-d51d75ed-2bf1-4f50-9cfa-0ab107701805.png">
* 해당 설정을 통해 Host는 각 VM에 가상 네트워크를 제공 가능하다.

Virtual Machine Network Configuration
=====================================
* Virtual Machine의 Network 설정 방법은 다음과 같이 8가지 방식으로 제공된다. 하나씩 뜯어보자.
  <img width="631" alt="image" src="https://user-images.githubusercontent.com/70207093/178915548-c3344b7c-73e8-4c8a-9c81-cf2a0bfb51e8.png">

* 연결되지 않음
* * 해당 VM의 LAN선을 뽑은 것과 같다.

* NAT (Network Address Translation) 방식
* * VM -> Host로 단방향 통신(물론 양방향 가능하다. 추가적인 설정을 통해서 포트포워딩을 수행해주어야 한다.)
* * Host 아래 Guest끼리의 통신이 불가능
* * 외부와 통신할 때, VM은 Host의 IP를 달고 통신한다. 

* NAT Network 방식
* * NAT 방식과 비슷하다. 차이점은 Guest끼리의 내부적인 통신이 가능하다.

* 브리지에 어댑터
* * Host PC와 동등한 수준의 네트워크 구성
* * 각 VM에 추가적인 IP 할당이 가능

