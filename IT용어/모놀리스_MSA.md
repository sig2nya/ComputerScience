* 출처 : https://www.n-ix.com/microservices-vs-monolith-which-architecture-best-choice-your-business/
* 우아한 형제들(배달의 민족)은 어떻게 MSA를 적용하였는가? : https://www.youtube.com/watch?v=BnS6343GTkY

Monolithic
==========
* 정의 : 하나의 소프트웨어를 구성하는 모든 모듈과 코드를 한 프로젝트 내에서 관리 -> 유지보수 어려움
  ![image](https://user-images.githubusercontent.com/70207093/176204367-d9d89639-f521-4bea-a52c-3c3686b16dfc.png)

* 예를 들어, 쇼핑몰을 하나 만든다고 하자.
```java
app/
 - domain/
 -- users/
 ---  model
 ---  repository
 -- products/
 ---  model
 ---  repository
 -- payment/
 ---  model
 ---  repository
 - service/
 -- user_service
 -- product_service
 -- payment_service
 - controller/
 -- user_controller
 -- product_controller
 -- payment_controller
 - main
 - config
```
* 쇼핑몰 구현을 위한 하나의 프로젝트에 모든 모듈과 관련 코드들이 존재
* 1) 장점 : 개발이 간단, 리뷰 Easy, 프로젝트 구성 단순, main만 실행시키면 되므로 배포 용이, 디버깅 및 장애 대응 쉬움
* 2) 단점 : 프로젝트 규모가 커짐 -> 유지보수 어려움, 모듈 및 코드간의 결합도가 높아짐, 프로젝트 전체에 대한 이해도 필요, 확장에 불리함(JAVA에서 왜 Interface를 사용하는지 생각하면 이해 가능)

Micro Service Architecture(MSA)
===============================
* 정의 : 모놀리틱(모놀리스)의 단점을 보완 가능 -> 프로젝트를 각각 독립된 모듈(프로젝트)로 개발 / 배포 / 테스트 수행 -> 변경과 확장에 용이
* * 예를 들어보자. 과거 갤럭시 / LG 옵티머스 스마트폰 모델이 배터리 일체형으로 나오기 시작했을 즘이었다. 사람들의 반발이 심했다. 
* * 왜? -> 배터리가 탈착형이었을때, 핸드폰이라는 기능에 배터리 탈착 수요가 많았기 때문. 즉, 사람들의 편리성 때문이었다.
* * 개발자가 핸드폰 사용자라고 해보자. 해당 프로젝트를 개발(사용)해야하는데, 변경이 어렵다(배터리 탈착이 안된다). 여기서 도출된 것이 MSA라고 생각한다.(비유가 적절했을지 모르겟다.)
    ![image](https://user-images.githubusercontent.com/70207093/176207196-149d568d-138a-4200-94c6-34eaa783ed8f.png)
* 위의 프로젝트 구조를 다음과 같이 바꿔보자
```java
# Users
- app/
--  domain/
---    model
--  service/
---    user_service
--  controller/
---    user_controller
--  main
--  config
```
```java
# Products
- app/
--  domain/
---    model
--  service/
---    product_service
--  controller/
---    product_controller
--  main
--  config
```
```java
# Payment
- app/
--  domain/
---    model
--  service/
---    payment_service
--  controller/
---    payment_controller
--  main
--  config
```
* 1) 장점 : 각 마이크로 서비스 별로 이해도가 쉬움, 각 프로젝트간 결합도 낮음, 테스트량도 마이크로서비스 단위로 작아짐, 기술 스택도 마이크로서비스 단위로 개발 가능, 확장에 용이.
* 2) 단점 : 통합 테스트 어려움, 관리 비용 증대 가능성, 전체적인 구조 파악 어려움, 분산 시스템이므로 해당하는 단점 존재.
