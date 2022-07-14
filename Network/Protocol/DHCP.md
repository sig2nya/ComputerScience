<h3>참고 URL : https://namu.wiki/w/DHCP</h3>

DHCP(Dynamic Host Configuration Protocol)
=========================================
* 개요 : IP 라우터는 인터페이스 및 호스트에 IP 주소를 할당 가능. 과거에는 IP를 고정적으로 할당 -> IP 충돌문제 야기
* 상기 언급한 문제 해결을 위해 DHCP를 이용하여 IP를 자동으로 할당하고, 미사용시에 해당 IP를 반환받아 재사용
* 라우터에 해당 기능 탑재가 가능하지만 DHCP Server를 두어 사용 가능
* 임대 - 갱신 - 반환 과정을 통하여 IP를 관리한다

Lease(임대)
===========
* 임대 : DHCP가 IP를 할당해주는 것
* 임대 기간이 끝나면 해당 IP는 DHCP 풀로 반환
* IP Time 공유기의 임대 기간은 보통 7200초로 설정됨
```java
상세과정
1. IP 주소가 할당되지 않은 호스트는 *Discover Packet*을 BroadCasting
   * 이 때, MAC Address 기반의 통신(당연하다. 호스트는 IP가 없기때문에, MAC 주소 기반으로 요청)
2. DHCP 서버가 이를 수신한다면 다음 과정 진행 / DHCP 외의 호스트는 해당 패킷을 폐기
3. DHCP는 *Offer Packet*을 BroadCasting / 요청한 호스트는 해당 패킷을 수신
4. 호스트가 *Offer Packet*을 수신한 후, *Request Packet*을 BroadCasting (DHCP Server가 여러개일 수 있기 때문)
5. DHCP Server는 DHCP ACK를 수행 / 즉, DHCP 풀에서 IP 주소를 호스트에게 임대
```

Linux Net_Conf
==============
> vi /etc/sysconfig/network-scripts/ifcfg-enp*** 수행 및 bootproto=dhcp 설정
> (해당 방법을 통해 네트워크 상에서 비어있는 ip를 동적으로 할당받을 수 있다. 또한, static 설정으로 통해 할당받은 ip를 정적으로 고정 가능)
  <img width="399" alt="image" src="https://user-images.githubusercontent.com/70207093/178936669-704f9f21-166e-485d-b4eb-04d2b44c2408.png">
