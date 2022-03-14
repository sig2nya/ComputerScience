URI(Uniform Resource Identifier)
================================
* 정의 : 자원을 식별한다. URI는 URL과 URN으로 구분된다. ex) 사람의 주민등록번호를 생각하면 된다.
* URL(Uniform Resource Location) : 장소를 의미한다. ex) foo://example.com:8042/over/there?name=ferret#nose
* URN(Uniform Resource Name) : 이름을 의미한다. ex) example:animal:ferret:nose
* * URN은 거의 사용되지 않으며, URL이 대부분이다.

> Uniform : 리소스를 식별하는 통일된 방식 / Resource : 자원, URI로 식별할 수 있는 모든 것 / Identifier : 다른 항목과 구분하는데 필요한 정보</br>
> URL 분석 : https://www.google.com/search?q=hello&hl=ko</br>
> > scheme://[userinfo@]host[:port][/path][?query][#fragment]</br>
> > - https://www.google.com/search?q=hello&hl=ko</br>
> > > - 주로 프로토콜 사용</br>
> > > 프로토콜 : 어떤 방식으로 자원에 접근할 것인가 약속 규칙
> > > httpsms 80포트, https는 443 포트를 주로 사용. 포트는 생략이 가능하다.
