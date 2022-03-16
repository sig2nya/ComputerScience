HTTP 상태 코드
============
* 1xx(Informational) : 요청이 수신되어 처리중... 거의 사용되지 않는다
* 2xx(Successful) : 요청 정상 처리
* 3xx(Redirection) : 요청을 완료하려면 추가 행동이 필요
* 4xx(Client Error) : 클라이언트 오류
* 5xx(Server Error) : 서버 오류

2xx - 성공
=========
* 200 : OK
* 201 : Created. 요청에 성공하여 새로운 리소스가 생성됨.
* 202 : Accepted. 요청이 접수되었으나, 완료되지 않음. 배치 처리 등에서 사용.
* 204 : No Content. 서버가 요청을 성공하였으나, 응답 페이로드 본문에 보낼 데이터가 없음. 웹 문서 편집기에서 save 버튼 등

3xx - 리다이렉션
=============
* 웹 브라우저는 3xx 응답 결과에 Location 헤더가 있으면, Location 위치로 자동 이동.
* 리디렉션의 이해 : 영구 리디렉션 - 특정 리소스의 URI가 영구적으로 이동 / 일시 리디렉션 - 일시적인 변경 / 특수 리디렉션 - 결과 대신 캐시를 사용
* 300 : Multiple Choices, 사용되지 않음.
* 301 : Moved Permanently, 리디렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음
* 308 : Permanent Redirect, 301과 기능은 같음. 리디렉트시 요청 메서드와 본문 유지(처음 POST를 보내면 리디렉트도 POST로 유지)
