HTTP_API
========
* POST 기반 등록(회원 관리 API 제공)
* * <b>회원</b> 목록 : /members -> GET
* * <b>회원</b> 등록 : /members -> POST
* * <b>회원</b> 조회 : /members/{id} -> GET
* * <b>회원</b> 수정 : /members/{id} -> PATCH, PUT, POST
* * <b>회원</b> 삭제 : /members/{id} -> DELETE

HTTP_API
========
* PUT 기반 등록
* * <b>파일</b> 목록 : /files -> GET
* * <b>파일</b> 조회 : /files/{filename} -> GET
* * <b>파일</b> 등록 : /files/{filename} -> PUT
* * <b>파일</b> 삭제 : /files/{filename} -> DELETE
* * <b>파일</b> 대량 등록 : /files -> POST

HTML_FORM
=========
* <b>회원</b> 목록 : /members -> GET
* <b>회원</b> 등록 폼 : /members/new -> GET
* <b>회원</b> 등록 : /members/new, /members -> POST
* <b>회원</b> 조회 : /members/{id} -> GET
* <b>회원</b> 수정 폼 : /members/{id}/edit -> GET
* <b>회원</b> 수정 : /members/{id} -> POST
* <b>회원</b> 삭제 : /members/{id} -> POST
