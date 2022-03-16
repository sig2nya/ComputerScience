HTTP Header
===========
* header-field = field-name ":" OWS field-value OWS (OWS : 띄어쓰기 허용)
* Field-name은 대소문자 구분 없음
* HTTP 전송에 필요한 모든 부가정보
* 예) 메시지 바디 내용 / 크기, 압축, 인증, 요청 클라이언트, 서버 정보, 캐시 관리 정보
* 표준 헤더가 너무 많고, 임의의 field 추가 가능

* HTTP Body
* * message body를 통해 표현 데이터 전달
* * 메시지 본문 = 페이로드
* * 표현은 요청이나 응답에서 전달할 실제 데이터
* * 표현 헤더는 표현 데이터를 해석할 수 있는 정보 제공(데이터 유형, 길이, 압축 정보)

* 표현 Header
* * Content-Type : 포현 데이터의 형식
* * Content-Encoding : 표현 데이터의 압축 방식
* * Content-Language : 포현 데이터의 자연 언어
* * Content-Length : 표현 데이터의 길이

* Content Negotiation
* * 정의 : 클라이언트가 선호하는 표현 요청
* * Accept : 클라이언트가 선호하는 미디어 타입 전달
* * Accept-Charset : 클라이언트가 선호하는 문자 인코딩
* * Accept-Encoding : 클라이언트가 선호하는 압축 인코딩
* * Accept-Language : 클라이언트가 선호하는 언어
* Quality Values 값을 이용. 0~1 클수록 높은 우선순위. 생략하면 1. 
* * Accept-Language : ko-KR, ko; q = 0.9, en-US; q = 0.8, en; q = 0.7
* 구체적인 것이 우선한다. 
* * Accept : text/*, text/plain, text/plain;format=flowed, */*
* 구체적인 것을 기준으로 미디어 타입을 맞춘다
* * Accept : text/*; q = 0.3, text/html; q = 0.7, text/html; level = 1, text/html; level = 2; q = 0.4, */*; q = 0.5

* 전송 방식
* * 단순 전송 / 압축 전송 / 분할 전송 / 범위 전송

* 일반 정보
* * From : 유저 에이전트의 이메일 정보, 요청에서 사용
* * Referer : 현재 요청된 페이지의 이전 페이지 주소. Referer를 사용해서 유입 경로 분석 가능(데이터 분석). (참고) Referer는 단어 referrer의 오타.
* * User-Agent : 클라이언트의 애플리케이션 정보(웹 브라우저), 어떤 종류의 브라우저에서 장애가 발생하는지 파악 가능(log parsing).
* * Server : 요청을 처리하는 ORIGIN 서버의 소프트웨어 정보.
* * Date : 메시지가 발생된 시간.

* 특별한 정보
* * Host(중요!) : 요청한 호스트 정보(도메인), 필수, 하나의 서버가 여러 도메인을 처리해야 할 때.
* * Allow : 허용 가능한 HTTP aptjem. 405에서 응답에 포함해야함.
* * Retry-After : 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간. 서비스가 언제까지 불능인지 알려줄 수 있음.

* 인증
* * Autorization : 클라이언트 인증 정보를 서버에 전달
* * WWW-Authenticate : 리소스 접근시 필요한 인증 방법 정의
