# URI와 웹 브라우저 요청 흐름
- URI
- 웹 브라우저 요청 흐름
<br></br>
## URI (Uniform Resource Identifier)
### `인터넷 자원을 나타내는 고유 식별자`

### URI, URL, URN의 차이는?  
### URI는 로케이터(locator), 이름(name) 또는 둘 다 추가로 분류될 수 있다.  
![2 uri-webbrowser pdf_page_05](https://user-images.githubusercontent.com/78770230/168061969-cf33db53-285d-4a3d-ac82-3b2c4ac9b74b.png)
URI는 리소스를 식별하는 방법, URI라는 개념 안에 URL, URN이 존재하는 것  
  
![2 uri-webbrowser pdf_page_06](https://user-images.githubusercontent.com/78770230/168062642-ea99c86a-f5a3-48f9-9c50-b26e506e355c.png)

URN사용 시 리소스 찾기가 힘들기 때문에 사실상 URL만 사용한다.  

### URI 단어 뜻

- Uniform: 리소스 식별하는 통일된 방식
- Resource: 자원, URI로 식별할 수 있는 모든 것(제한 없음)
- Identifier: 다른 항목과 구분하는데 필요한 정보
<br></br>
- URL: Uniform Resource Locator
- URN: Uniform Resource Name

### URL, URN 단어 뜻

- URL - Locator: 리소스가 있는 위치를 지정
- URN - Name: 리소스에 이름을 부여
- 위치는 변할 수 있지만, 이름은 변하지 않는다.
- urn:isbn:8960777331 (어떤 책의 isbn URN)
- URN 이름만으로 실제 리소스를 찾을 수 있는 방법이 보편화 되지 않음
- 그러므로 URI를 URL과 같은 의미로 이야기하겠음  
<br></br>
## URL 전체 문법  
  
- scheme://[userinfo@]host[:port][/path][?query][#fragment]
- https://www.google.com:443/search?q=hello&hl=ko
<br></br>
- 프로토콜(https)
- 호스트명(www.google.com)
- 포트 번호(443)
- 패스(/search)
- 쿼리 파라미터(q=hello&hl=ko)
<br></br>
### scheme
- 주로 프로토콜 사용
- 프로토콜: 어떤 방식으로 자원에 접근할 것인가 하는 약속 규칙
  - 예) http, https, ftp 등
- http는 80포트, https는 443 포트를 주로 사용, 포트는 생략 가능
- https는 http에 보안 추가 (HTTP Secure)
<br></br>
### userinfo
- URL에 사용자정보를 포함해서 인증
- 거의 사용하지 않음
<br></br>
### host
- 호스트명
- 도메인명 또는 IP 주소를 직접 사용가능
<br></br>
### PORT
- 포트(PORT)
- 접속 포트
- 일반적으로 샹략, 생략시 http는 80, https는 443
<br></br>
### path
- 리소스 경로(path), 계층적 구조
- 예)
  - /home/file1.jpg
  - /members
  - /members/100, /items/iphone12
<br></br>
### query
- key=value 형태
- ?로 시작, &로 추가 가능 ?keyA=valueA&keyB=valueB
- query parameter, query string 등으로 불림, 웹서버에 제공하는 파라미터, 문자 형태
<br></br>
### fragment
- fragment
- html 내부 북마크 등에 사용
- 서버에 전송하는 정보 아님
<br></br><br></br>

출처 : 모든 개발자를 위한 HTTP 웹 기본 지식 : <https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC>,
