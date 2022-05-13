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
<br></br>
## 웹 브라우저 요청 흐름
![2 uri-webbrowser pdf_page_19](https://user-images.githubusercontent.com/78770230/168277212-7dc764ec-9f5e-41ea-a62f-38f511c4eb47.png)  
![2 uri-webbrowser pdf_page_20](https://user-images.githubusercontent.com/78770230/168277273-91f07aba-5bd4-4d4d-ac75-7fdd097cdb81.png)  
- 먼저 웹 브라우저는 DNS서버를 조회해서 IP, PORT정보를 찾아낸다.
- HTTP 요청 메세지 생성한다.
<br></br>

### 간략화된 HTTP 요청 메세지
![2 uri-webbrowser pdf_page_21](https://user-images.githubusercontent.com/78770230/168278160-37e6f8c1-fd36-4962-80ba-efa3a11cd882.png)
<br></br>
### HTTP 메세지 전송
![2 uri-webbrowser pdf_page_22](https://user-images.githubusercontent.com/78770230/168278353-6c7ba20e-00c1-435b-89d8-af8a86d516ac.png)
- 브라우저가 생성한 HTTP메세지를 SOCKET 라이브러리를 통해 OS에 전달한다.
  - 위에서 찾은 IP와 PORT정보를 통해 TCP/IP의 3way handshaking을 통해 구글 서버와 연결한다.
  - 그리고 해당 데이터를 전달한다.
- HTTP메세지에 IP와 PORT정보가 들어있는 패킷을 씌워서 인터넷 망으로 전달한다.

![2 uri-webbrowser pdf_page_23](https://user-images.githubusercontent.com/78770230/168279341-94685d2a-bfa8-4e9b-97f0-d38d3c5b34b1.png)
![2 uri-webbrowser pdf_page_24](https://user-images.githubusercontent.com/78770230/168279338-57c0f34f-38ea-43c7-836c-f13ffe501893.png)
- 전송 데이터는 웹 브라우저가 만든 HTTP 메세지이다.
<br></br>

![2 uri-webbrowser pdf_page_25](https://user-images.githubusercontent.com/78770230/168279734-fcf1bb4e-a60e-4edc-b372-119897b17d91.png)
![2 uri-webbrowser pdf_page_26](https://user-images.githubusercontent.com/78770230/168279745-6f43cdd7-1074-4562-9c96-4d7e2c99df9e.png)
- 생성된 패킷을 인터넷 망을 통해 전달하면 수 많은 인터넷 노드들을 통해서 서버로 전달이 된다.
- 요청 패킷이 서버에 도착하면, 서버에서는 해당 패킷 안에있는 HTTP 메세지를 꺼내서 해석한다.
- 해석 후 요청에 따라 HTTP응답 메세지를 생성한다.


### 간략화된 HTTP 응답 메세지
![2 uri-webbrowser pdf_page_27](https://user-images.githubusercontent.com/78770230/168280407-80e21cca-da93-45c5-b7c5-9dc051628b2e.png)
<br></br>
![2 uri-webbrowser pdf_page_28](https://user-images.githubusercontent.com/78770230/168280450-ae8122b3-820a-4fd4-9417-7b823bf99882.png)
![2 uri-webbrowser pdf_page_29](https://user-images.githubusercontent.com/78770230/168280456-d98c2168-f64a-4f97-8eb2-78bfa1fb94e8.png)
- 서버도 같은 방식으로 응답 패킷을 생성하고 클라이언트에 인터넷 망을 통해 전달한다.

![2 uri-webbrowser pdf_page_30](https://user-images.githubusercontent.com/78770230/168280552-9c7fde9c-93f2-4e61-a863-98bb9972574d.png)
- 웹 브라우저는 수신한 응답 패킷 안에 메세지를 꺼내고, 해당 메세지에 있는 HTML을 렌더링해서 보여준다.
<br></br><br></br>

출처 : 모든 개발자를 위한 HTTP 웹 기본 지식 : <https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC>,
