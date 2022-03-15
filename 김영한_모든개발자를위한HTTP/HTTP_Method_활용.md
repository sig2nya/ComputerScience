Client->Server로 Data전송
=======================
* Query String 이용 : GET 이용, 정렬 필터
* Message Body 이용 : POST, PUT, PATCH 이용, 회원 가입, 상품 주문, 리소스 등록, 리소스 변경
* 크게 4가지 상황  
* * 정적 데이터 조회 : 이미지, 정적 데이터 조회, GET 이용, Query String 없이 리소스 경로로 단순 조회
* * 동적 데이터 조회 : Query String 이용, Query String 기반으로 정렬 필터하여 결과를 동적으로 생성, 주로 검색, 게시판 목록 정렬, GET 이용, Query String을 사용하여 데이터를 전달.
* * HTML Form을 통한 데이터 전송 : HTML Form을 이용하여 POST 전송, default content-type : application/x-www-form-urlencoded
* * * multipart/form-data : 파일을 전송할 때 사용하는 Content-type
* * HTTP API를 통한 데이터 전송 : Client에 Library를 이용(대부분 다 있음), 앱 Client(아이폰, 안드로이드), AJAX, React, VuewJS, POST/PUT/PATCH 활용 가능, Content-Type : application/json을 주로 이용.
