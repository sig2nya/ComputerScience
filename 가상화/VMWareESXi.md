ESXi
====
* ESXi : VMWare 사에서 출시한 하이퍼바이저 및 유닉스 계열의 운영체제(보통, 서버용)
* ESXi가 설치된 서버에 WEB을 통하여 접속하면 다음과 같은 UI 확인 가능
  <img width="1280" alt="image" src="https://user-images.githubusercontent.com/70207093/176096323-370333c1-c0bd-4b60-a8bf-bbb7b686e5eb.png">

ESXi UI
=======
* root 권한으로 Login을 수행하게 되면, 다음과 같이 Server측 자원 확인 가능
  <img width="481" alt="image" src="https://user-images.githubusercontent.com/70207093/176097231-ca40e5e1-6a2e-4644-a710-a3d3f9f5eabe.png">

* ESXi를 통하여 .ova 파일과 같은 솔루션들을 Deployment 진행 가능
* ESXi를 통하여 Virtual Machine 관리를 용이하게 가능(Solution Deployment에 유용하게 쓰였다. 배포 이후에는 Putty와 같은 SSH를 이용하여 해당 솔루션을 관리하였다. *웬만하면 배포 이후에는 ESXi를 통해 작업하는 걸 추천 못하겟다.)

Docker / Virtual Machine
========================
* Docker와 Virtual Machine의 차이
* 1) Virtual Box를 생각해보자. Virtual Box라는 Hypervisor 위에 이미지를 생성한다. 해당 머신 위에 사용하고자하는 OS(Guest OS)를 설치해야한다. 하지만, 도커는 그럴 필요 없다.
* 2) 더 나아가, Hypervisor 기반의 VM은 Hypervisor 위에 새로운 VM이 생성될 때마다 그에 맞는 OS를 설치해야한다. 이는 비효율적이다. 이에 반해, 다음 도커의 특징을 살펴보면 가상화와의 차이점을 명확히 알 수 있다. (출처 : <a href="https://namu.wiki/w/Docker">나무위키</a>)
  <img width="730" alt="image" src="https://user-images.githubusercontent.com/70207093/176098091-a9713911-6e12-4fd5-86d2-543e465f7168.png">

* 첫 번째 특징에서도 잘 나와있다. 운영체제를 가상화 하지 않는다고 되어있다. 가상머신에 비해 매우 가벼울 것이다.
* 아래는 Docker와 Hypervisor에 대한 차이점을 그림으로 나타낸 것이다. Guest OS에서 차이가 있는 것을 확인할 수 있다.

  <img width="579" alt="image" src="https://user-images.githubusercontent.com/70207093/176097415-448ffd10-a35a-426f-8a7d-36ebddab6855.png">
