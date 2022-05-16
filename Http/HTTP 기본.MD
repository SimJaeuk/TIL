# HTTP 기본
- HTTP
- 클라이언트 서버 구조
- Stateful, Stateless
- 비 연결성(connectionless)
- HTTP 메세지
<br></br>
## HTTP (HyperText Transfer Protocol)
### `HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 프로토콜`<br></br>

## 모든 것이 HTTP (HTTP 메세지에 모든 것을 전송)<br></br>
- HTML, TEXT
- IMAGE, 음성, 영상, 파일
- JSON, XML (API)
- 거의 모든 형태의 데이터 전송 가능
- 서버간에 데이터를 주고 받을 때도 대부분 HTTP 사용
  - 실무에서 서버간에 TCP를 직접 연결하는 경우는 거의 없음
  - 게임서버 혹은 특수한 경우에만 TCP를 직접 연결
- **지금은 HTTP 시대!**
<br></br><br></br>
### HTTP 역사<br></br>
- HTTP/0.9 1991년: GET 메서든만 지원, HTTP 헤더X
- HTTP/1.0 1996년: 메서드, 헤더 추가
- **HTTP/1.1 1997년: 가장 많이 사용, 우리에게 가장 중요한 버전**
  - RFC2068 (1997) -> RFC2616 (1999) -> RFC7230~7235 (2014)
- HTTP/2 2015년: 성능 개선
- HTTP/3 진행중: TCP 대신에 UDP 사용, 성능 개선

> HTTP/1.1이 가장 중요한 이유는 2와 3은 성능개선이므로 1.1과 큰 차이가 없기 때문이다.
> <br></br>
### 기반 프로토콜

- TCP: HTTP/1.1, HTTP/2
- UDP: HTTP/3
- 현재 HTTP/1.1 주로 사용
  - HTTP/2, HTTP/3도 점점 증가
<br></br>
### HTTP 특징
- 클라이언트 서버 구조
- 무상태 프로토콜(스테이스리스), 비연결성
- HTTP 메세지
- 단순함, 확장 가능
<br></br>



<br></br><br></br>

출처 : 모든 개발자를 위한 HTTP 웹 기본 지식 : <https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC>,
