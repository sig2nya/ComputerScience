Docker로 MySQL 실행
===================
* 1) docker run -it --name mysql -e MYSQL_ROOT_PASSWORD=Avaya123$ -e MYSQL_DATABASE=dockerdb mysql 명령어 수행
* <img width="626" alt="image" src="https://user-images.githubusercontent.com/70207093/176130654-3e7b95b8-dc3a-4d7d-8045-9affe3551331.png">

* 2) 새로운 Terminal 창 -> docker ps
* <img width="716" alt="image" src="https://user-images.githubusercontent.com/70207093/176130856-2cce1df2-d1c7-4aff-baf5-0480c3985c81.png">

* 3) Container exec
* <img width="722" alt="image" src="https://user-images.githubusercontent.com/70207093/176131272-8d2e680e-7f02-4072-88a5-6b1862ada89a.png">

* 4) Terminal을 통한 MySQL 접속
* <img width="720" alt="image" src="https://user-images.githubusercontent.com/70207093/176131689-2e845170-3e1a-487e-b7ef-d1b50cb104d3.png">

* 5) Test용 DB를 만들어 주었다.
* <img width="722" alt="image" src="https://user-images.githubusercontent.com/70207093/176131858-453a50c1-4be9-4f8d-b5d7-6135a0f70a49.png">

* 이제 해당 DB에 접속하는 방법을 찾아야 할 것 같다.
