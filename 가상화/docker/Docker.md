Docker 설치
===========
* 실행 환경 : Ubuntu 20.04 on Windows
* 1) cmd에서 Ubuntu 20.04 설치 수행(설치가 안된다면 cmd를 관리자 권한으로 수행) -> wsl --install -d Ubuntu-20.04 명령어 실행
* <img width="694" alt="image" src="https://user-images.githubusercontent.com/70207093/176104009-d8a56bed-1421-4ebb-a498-b37cf69bfc57.png">

* 2) root 계정 생성(설치가 완료되면 자동으로 아래 화면이 나온다)
* <img width="721" alt="image" src="https://user-images.githubusercontent.com/70207093/176105410-4c572c37-ab3c-4f6b-85fa-45153bc39225.png">

* 3) apt update 먼저 조져주자.
* <img width="625" alt="image" src="https://user-images.githubusercontent.com/70207093/176105634-53bcedd9-0c14-4d83-aaf4-2f84473e3bf8.png">

* 4) docker.io Installation
* <img width="626" alt="image" src="https://user-images.githubusercontent.com/70207093/176105963-b758e950-3775-4cfe-adea-82507636bad7.png">

* 5) docker.io가 설치가 되었다면, sudo dockerd를 통하여 실행시키자(좌측 화면). Docker Deamon을 실행시키는 명령어이다.
* 6) Ubuntu terminal을 하나 더 띄워, sudo docker hello-world 명령어를 수행한 뒤에, 'Hello from Docker!'가 나오면 Docker 설치가 끝.(우측 화면)
* <img width="1266" alt="image" src="https://user-images.githubusercontent.com/70207093/176106884-4019a6a0-dd71-4668-9c08-a9514dd180fc.png">
