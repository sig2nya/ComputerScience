FailOver(장애 극복)
===================
* Design for Failure : 장애는 반드시 발생한다는 전제로 시스템 설계
* 시스템 이중화를 통한 HA 보장
* 궁극적으로, 이중화를 통하여 장애에 따른 손실 비용 절감

시스템 정상 가동
===============
<img width="476" alt="image" src="https://user-images.githubusercontent.com/70207093/173295067-894e7149-6083-4762-84d1-88a91530724c.png">

```java
// Shell Script
#!/bin/sh
VIP='192.168.0.0'
DEV='enp0s3'

healthCheck(){
  ping -c 1 -w 1 $VIP > /dev/null
  return $?
} // Virtual IP의 상태를 확인하는 함수

ip_takeOver(){
        IP=$(ip addr show | grep $DEV | egrep -o '([0-9]{1,3}.){3}[0-9]{1,3}' | head -1)
        ip addr add $VIP/24 dev $DEV
        echo "$VIP is designated to $IP:$DEV"
} // Virtual IP가 Down 되었을 때(Ping이 도달하지 않으면), 해당 Virtual IP를 TakeOver 수행
```

Master System Down
==================
<img width="441" alt="image" src="https://user-images.githubusercontent.com/70207093/173295759-705af385-648a-49d6-9a98-f51df0eba567.png">

```java
// Master에 대한 Ping 상태 확인
#!/bin/sh
ip_pingchack() {
        ping -c 1 -w 1 192.168.0.0(MasterIP) > /dev/null
                return $?
}
// 만약, Master System이 정상 구동 한다면, ifconfig enp0s3를 up / down 시켜서 SLAVE의 Virtual IP 할당 해제
```
