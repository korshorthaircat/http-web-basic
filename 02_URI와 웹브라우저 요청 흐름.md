# URI와 웹 브라우저 요청 흐름
## URI
* URI(Uniform Resource Identifier) - 리소스를 식별하는 통합된 방법
	* URI의 의미
		* Uniform: 리소스를 식별하는 _통일된_방식
		* Resource: 자원(URI로 식별할 수 있는 모든 것)
		* Identifier: 다른 항목과 구분하기 위해 필요한 정보
* URI / URL / URN의 구분
	* “URI는 로케이터(locator), 이름(name) 또는 둘 다 추가로 분류될 수 있다.”
	* URI(Uniform Resource _Identifier_)
		* URL(Uniform Resource _Locator_) - 리소스가 있는 위치를 지정
		* URN(Uniform Resource _Name_) - 리소스에 이름을 부여
			* 예) urn:isbn:8960777331(어떤 책의 isbn URN)
	* URN 이름 만으로 실제 리소스를 찾을 수 있는 방법이 보편화되지 않았음 -> URL을 주로 사용함,  따라서 URI와 URL을 같은 의미로 말해도 무방함.
```
URL
foo://example.com:8042/over/there?name=ferret#nose

URN
urn:example:animal:ferret:nose
```

* URL의 분석
	* URL의 구조와 예시
```
scheme://[userinfo@]host[:port][/path][?query][#fragment]

https://www.google.com:443/search?q=hello&hl=ko
  	* 프로토콜 - https
	* 호스트명 - www.google.com
	* 포트 번호 - 443
	* 패스 - /search
	* 쿼리 파라미터 - q=hello&hl=ko
```		




* URL의 문법
	* scheme
		* 주로 프로토콜 사용. 
			* 프로토콜 - 어떤 방식으로 자원에 접근할 것인가 하는 약속, 규칙
			* 예) http, https(HTTP Secure), ftp 등
		* http는 80포트, https는 443포트를 주로 사용함. 포트는 생략 가능.
	* userinfo 
		* URL에 사용자 정보를 포함해서 인증함
		* 거의 사용하지 않음
	* host
		* 도메인명 또는 IP 주소를 직접 사용 가능
	* port
		* 접속 포트. (https는 80, https는 443)  
		* 일반적으로 생략함
	* path
		* 리소스 경로(path), 계층적 구조
		* 예) /items/iphone12
	* query
		* key=value 형태, ?로 시작, &로 추가 가능 
			* ?keyA=valueA&keyB=valueB
		* query parameter, query string 등으로 불림
	* fragment
		* html 내부 북마크 등에 사용됨
		* 서버에 전송하는 정보가 아님

## 웹 브라우저 요청 흐름
* 웹브라우저의 주소창에 `‘https://www.google.com/search?q=hello&hl=ko'` 를 입력하고 엔터를 누르면…
	* 웹브라우저가 도메인명`(www.google.com)`을 DNS 조회하여 IP를 얻음
	* HTTP 요청 메세지를 생성함(TCP/IP 패킷을 생성할 때, HTTP 요청 메시지가 포함됨)
	* 요청 패킷이 수많은 인터넷 노드를 통해 이동하다가 서버에 전달됨 
	* 서버는 HTTP 응답 메시지를 생성하여 응답 패킷을 전송함
	* 도착한 응답패킷을 웹브라우저가 HTML 렌더링하여 화면에 띄움
