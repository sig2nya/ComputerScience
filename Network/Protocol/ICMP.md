* 참조 : https://www.ibm.com/docs/ko/aix/7.1?topic=protocols-internet-control-message-protocol

ICMP
====
* 개요 : ICMP(Internet Control Message Protocol)이란 모든 IP 구현의 필수 부분이다. ICMP는 오류를 처리하고 IP 메시지를 제어한다.
* 역할 : 대상이 활성 상태이고, 도달 가능한지 여부 확인 / 데이터 그램 헤더의 매개변수 문제점 보고 / 클럭 동기화 및 통과 시간 예상 수행 / 인터넷 주소 및 서브넷 마스크 확보 
* ICMP 메시지는 다음의 경우 전송 가능 : 패킷이 대상에 도달할 수 없을 때 / 게이트웨이 호스트에 패킷을 전달할 버퍼링 용량이 없을 경우 / 게이트웨이가 호스트에 보다 짧은 라우트로 트래픽을 전송하도록 지시할 수 있을 때

