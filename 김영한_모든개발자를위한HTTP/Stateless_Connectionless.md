HTTP Stateless
==============
* Stateless는 서버 증설에 유리하다.
* 서버가 바뀌어도 상관 없이 같은 서비스를 제공 가능하다.(고객응대에 빗대어 비유해보자. 한 점원이 고객을 응대하다가, 다른 점원이 고객을 응대할 수 있다.)
* 갑자기, 고객이 대거 증가하여도 점원을 대거 투입 가능하다. 즉, 트래픽이 증가하여도 서버를 증설하여 요청을 처리할 수 있다.
* Stateful은 어떠한 서비스에 대해 항상 같은 서버가 유지되어야 할 것이다. 이 때, 해당 서비스를 담당하는 서버가 다운된다면 서비스 제공이 아예 불가능하다.
* Stateless는 대체할 서버 증설 용이가 수월하다는 것이다.

HTTP Connectionless
===================
* Server-Client 간의 통신이 끝나면 연결을 끊는 모델.
* HTTP는 Connectionless이다.
* 다양한 Clients가 서비스를 사용하므로 Server가 처리해야하는 요청은 매우 커짐
* 연결이 필요할때만 연결하여 자원을 효율적으로 사용 가능.
