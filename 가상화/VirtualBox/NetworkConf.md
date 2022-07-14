* 참고 : https://technote.kr/213

Virtual Box Network Configuration
=================================
* 개요 : Virtual Box로 가상화를 구성하는데 Host를 통한 네트워크 접근, VM 자체로부터 네트워크 접근 등 좀 더 세부적으로 네트워크 설정 방법을 공부하고자 작성.(VM 구축 중에 yum이 안먹는다. 확인해보니 네트워크 연결 자체가 안되서 해당 부분에 대한 이해가 필요하다 느낌)
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
* * WIFI 공유기 또한 NAT 방식으로 내부 네트워크에 IP를 할당한다. VirtualBox의 NAT 방식도 마찬가지이며, Host PC가 공유기 역할을 하여 VM들에게 IP를 할당해준다.
* * 이는, Host IP가 공인 IP가 되어 외부에서의 접근이 어려워진다. 즉, VM -> Host로 단방향 통신이 된다.(양방향 또한 물론 가능하다. 추가적인 설정을 통해서 포트포워딩을 수행해주어야 한다.)
* * Host 아래 Guest끼리의 통신이 불가능
* * 외부와 통신할 때, VM은 Host의 IP를 달고 통신한다.
* * 위의 특징들에 기반하여 NAT 방식은 VM을 Client로써 사용할 때 적합하다. 즉, NAT 방식은 Server로 사용하기 매우 부적합한 네트워크 방식.

* NAT Network 방식
* * NAT 방식과 비슷하다. 차이점은 Guest끼리의 내부적인 통신이 가능하다.

* 브리지에 어댑터
* * Host PC와 동등한 수준의 네트워크 구성
* * 각 VM에 추가적인 IP 할당이 가능

