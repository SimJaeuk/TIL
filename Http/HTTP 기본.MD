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

## 클라이언트 서버 구조<br></br>

- Request Response 구조
- 클라이언트는 서버에 요청을 보내고, 응답을 대기
- 서버가 요청에 대한 결과를 만들어서 응답
<br></br>
![20220517190850](https://user-images.githubusercontent.com/78770230/168787431-fa234265-7481-482c-bbd2-38dfd277f960.png)
<br></br>

표면적으로 보기 단순한 구조이지만, 이렇게 **분리**를 하는것은 굉장히 중요하다.  
예전에는 클라이언트와 서버가 분리되어 있지 않았는데, 클라이언트와 서버를 개념적으로 분리 해낸 후  
서버는 비지니스 로직과 데이터, 클라이언트는 UI/UX에 집중했다.  
> 이렇게 함으로써 클라이언트와 서버가 각각 독립적으로 발전할 수 있는 장점이 있다.  

클라이언트는 복잡한 비즈니스 로직, 데이터를 다룰 필요 없이 단순하게 화면과 사용성에 집중할 수 있고  
서버도 트래픽이 폭주할 일이 있어도 클라이언트는 손 댈 필요 없이 서버의 아키텍트와 백앤드에서 트래픽을 어떻게 처리할지만 고민하면 된다.
<br></br>
## 무상태 프로토콜 (Stateless) <br></br>
- 서버가 클라이언트의 상태를 보존하지 않음
- 장점 : 서버 확장성이 높음(스케일 아웃)
- 단점 : 클라이언트가 추가 데이터 전송
<br></br>

## Stateful, Stateless 차이<br></br>
### 상태 유지 - Stateful
- 고객 : 이 **노트북** 얼마인가요?
- 점원 : 100만원 입니다.
<br></br>

- 고객 : **2개** 구매하겠습니다.
- 점원 : 200만원 입니다. **신용카드, 현금**중에 어떤 걸로 구매 하시겠어요?
<br></br>

- 고객 : **신용카드**로 구매하겠습니다.
- 점원 : 200만원 결제 완료되었습니다.
<br></br>

### 상태 유지 - Stateful, 점원이 중간에 바뀌면?
- 고객 : 이 **노트북** 얼마인가요?
- 점원**A** : 100만원 입니다.
<br></br>

- 고객 : **2개** 구매하겠습니다.
- 점원**B** : ? 무엇을 2개 구매하시겠어요?
<br></br>

- 고객 : **신용카드**로 구매하겠습니다.
- 점원**C** : ? 무슨 제품을 몇개 신용카드로 구매하시겠어요?
<br></br>

### 상태 유지 - Stateful, 정리
- 고객 : 이 **노트북** 얼마인가요?
- 점원 : 100만원 입니다. **(노트북 상태 유지)
<br></br>

- 고객 : **2개** 구매하겠습니다.
- 점원 : 200만원 입니다. **신용카드, 현금**중에 어떤 걸로 구매 하시겠어요?  
         **(노트북, 2개 상태 유지)
<br></br>
- 고객 : 신용카드로 구매하겠습니다.
- 점원 : 200만원 결제 완료되었습니다. **(노트북, 2개, 신용카드 상태 유지)**

<br></br>

### 무상태 - Stateless
- 고객 : 이 **노트북** 얼마인가요?
- 점원 : 100만원 입니다.
<br></br>

- 고객 : **노트북 2개** 구매하겠습니다.
- 점원 : 노트북 2개는 200만원 입니다. **신용카드, 현금**중에 어떤 걸로 구매 하시겠어요?
<br></br>

- 고객 : **노트북 2개를 신용카드**로 구매하겠습니다.
- 점원 : 200만원 결제 완료되었습니다.

<br></br>

### 무상태 - Stateless, 점원이 중간에 바뀌면?
- 고객 : 이 **노트북** 얼마인가요?
- 점원**A** : 100만원 입니다.
<br></br>

- 고객 : **노트북 2개** 구매하겠습니다.
- 점원**B** : 노트북 2개는 200만원 입니다. **신용카드, 현금**중에 어떤 걸로 구매 하시겠어요?
<br></br>

- 고객 : **노트북 2개를 신용카드**로 구매하겠습니다.
- 점원**C** : 200만원 결제 완료되었습니다.
<br></br>

### 정리
- **상태 유지:** 중간에 다른 점원으로 바뀌면 안된다.
  - 중간에 다른 점원으로 바뀔 때 상태 정보를 다른 점원에게 미리 알려줘야 한다.
- **무상태:** 중간에 다른 점원으로 바뀌어도 된다.
  - 갑자기 고객이 증가해도 점원을 대거 투입할 수 있다.
  - 갑자기 클라이언트 요청이 증가해도 서버를 대거 투입할 수 있다.
- 무상태는 응답 서버를 쉽게 바꿀 수 있다. -> **무한한 서버 증설 가능**
<br></br>

### 확장 가능
![3 http pdf_page_15](https://user-images.githubusercontent.com/78770230/169030498-3a095f02-57f8-46c3-b59c-8a84b992529a.png)
- 클라이언트 A는 계속 서버1번과 통신을 해야한다.
<br></br>

![3 http pdf_page_16](https://user-images.githubusercontent.com/78770230/169030615-26c8c90e-52b8-487a-8559-9fc644635324.png)
- 유지되던 상태정보가 다 날아가버리므로 처음부터 다시 요청해야한다.
<br></br>
![3 http pdf_page_17](https://user-images.githubusercontent.com/78770230/169031141-06f29384-f2be-41af-a424-0e58eca91fac.png)
- 요청할 때 필요한 데이터를 다 담아서 요청하기 때문에, 아무 서버나 호출해도 된다.
<br></br>
![3 http pdf_page_18](https://user-images.githubusercontent.com/78770230/169031280-426329be-923d-4c7e-8101-88e7a54da956.png)
- 중계서버가 다른 서버로 요청하면 되기때문에 처음부터 다시 요청할 필요가 없다.
<br></br>
![3 http pdf_page_19](https://user-images.githubusercontent.com/78770230/169031473-0fd131fd-7278-4e0f-9ea0-aed79e6b16f9.png)

### Stateless 실무 한계
- 모든 것을 무상태로 설계할 수 있는 경우도 있고 없는 경우도 있다.
- 무상태
  - 예) 로그인이 필요 없는 단순한 서비스 소개 화면
- 상태 유지
  - 예) 로그인
- 로그인한 사용자의 경우 로그인 했다는 상태를 서버에 유지
- 일반적으로 브라우저 쿠키와 서버 세션등을 사용해서 상태 유지
- 상태 유지는 최소한만 사용해야한다.
- 데이터를 너무 많이 보낸다는 단점이 있다.

## 비 연결성(Connectionless) <br></br>

### 연결을 유지하는 모델
![3 http pdf_page_22](https://user-images.githubusercontent.com/78770230/169284795-5acd2208-4c13-4e8e-aee6-0af7f7a26fda.png)
![3 http pdf_page_23](https://user-images.githubusercontent.com/78770230/169284800-412accff-03a9-4e05-a540-69570a00b761.png)
![3 http pdf_page_24](https://user-images.githubusercontent.com/78770230/169284808-a2e21b9d-ed07-45c6-b252-42020f793e2b.png)
- TCP/IP 연결의 경우 기본적으로 연결을 유지한다.
- 클라이언트 2,3은 요청을 보내지 않더라도 계속 연결을 유지하고 있다.
- 연결을 유지하는 서버의 자원이 계속 소모가 된다.
<br></br>

### 연결을 유지하지 않는 모델<br></br>
![3 http pdf_page_26](https://user-images.githubusercontent.com/78770230/169288845-8432decc-1ca2-44eb-a825-141bd1ac0983.png)
![3 http pdf_page_27](https://user-images.githubusercontent.com/78770230/169288856-cdd987b1-bb93-4917-bbc2-50e5445fc054.png)
![3 http pdf_page_28](https://user-images.githubusercontent.com/78770230/169288860-e4d1dc06-1a0b-4152-98c9-81c29907483b.png)
![3 http pdf_page_29](https://user-images.githubusercontent.com/78770230/169288866-6301ea25-8e9a-4e6a-95f5-77c8a49f86fa.png)


- 요청을 주고 받을 때에만 연결을 유지한다. 
- 서버유지에 필요한 자원을 최소한으로 줄여준다.
<br></br>

### 연결을 유지하지 않는 모델
- HTTP는 기본적으로 연결을 유지하지 않는 모델이다.
- 일반적으로 초 단위 이하의 빠른 속도로 응답한다.
- 1시간 동안 수천명이 서비스를 사용해도 실제 서버에서 동시에 처리하는 요청은 수십개 이하로 매우 작다.
  - 예) 웹 브라우저에서 계속 연속해서 검색 버튼을 누르지는 않는다.
- 서버 자원을 매우 효율적으로 사용할 수 있음
<br></br>

### 비 연결성의 한계와 극복
- 요청이 있을 때마다 TCP/IP 연결을 새로 맺어야 한다. - 3 way handshake 시간 추가
- 웹 브라우저로 사이트를 요청하면 HTML 뿐만 아니라 자바스크립트, CSS, 추가 이미지 등 수 많은 자원이 함께 다운로드
  - 수 많은 자원들을 보낼때마다 연결을 했다가 끊었다가 반복하는 것은 비효율
- 지금은 HTTP 지속 연결(Persistent Connections)로 문제 해결
- HTTP/2, HTTP/3에서 더 많은 최적화
<br></br>



### HTTP 초기 - 연결, 종료 낭비
![3 http pdf_page_33](https://user-images.githubusercontent.com/78770230/169287366-61e48b88-dab7-454b-9131-35ec2f62dcda.png)
<br></br>

### HTTP 지속 연결(Persistent Connections)
![3 http pdf_page_34](https://user-images.githubusercontent.com/78770230/169287502-e7480ad1-3167-4a40-bef5-a4a8870fff2a.png)
<br></br>

### 스테이스리스를 기억하자
#### 서버 개발자들이 어려워하는 업무

- 같은 시간에 딱 맞추어 발생하는 대용량 트래픽
  - 예) 선착순 이벤트, 명절 KTX 예약, 학과 수업 등록
- 비 연결성이 소용 없다. (동시 요청으로 몰리기 때문)
<br></br>

> 최대한 Stateless하게 설계해야한다.  
> 그래야만 이런 대용량 트래픽이 올 때에도 서버를 한번에 늘려서 대응할 수 있는 부분이 많아진다.
>> 무상태로 갈 수 있는 부분은 최대한 무상태로 가고 어쩔 수 없는 부분에 한해서 상태유지를 하도록 잘 분리해서 설계하는게 중요하다.
<br></br>

## HTTP 메세지
### `클라이언트와 서버 사이에서 데이터와 교환되는 방식`
<br></br>

### HTTP는 요청메세지와 응답메세지의 구조가 조금 다르다.
![20220520194712](https://user-images.githubusercontent.com/78770230/169512440-1a4a5ee7-9876-4adf-8193-15f4caac6132.jpg)
- 시작 라인, 헤더, **공백 라인**(필수), 메세지 바디로 이루어져 있음
<br></br>

![20220520194719](https://user-images.githubusercontent.com/78770230/169512567-1e614a47-2b60-4da0-9e13-5fef50cc00ac.jpg)
- 요청 메세지도 body 본문을 가질 수 있음
- 메세지 바디가 없다면 공백으로 놓고 끝내면 됨
<br></br>

![20220520194723](https://user-images.githubusercontent.com/78770230/169512592-7aae5410-897d-4b07-bd35-6ba9730596ce.jpg)

### 시작 라인
- 크게 request-line과 status-line이 있다.
- 요청 메세지는 request-line, 응답은 status-line
<br></br>

### 요청 메세지
- request-line = method SP request-target SP HTTP-version CRLF(엔터)
![20220520195445](https://user-images.githubusercontent.com/78770230/169513611-a8047ded-463e-4851-956a-9907dafd3fa7.jpg) 
- HTTP 메서드 (GET: 조회)
- 요청 대상(/search?q=hello&hl=ko)
- HTTP Version
<br></br>

### HTTP 메서드
- 종류: GET, POST, PUT, DELETE...
- 서버가 수행해야 할 동작 지정
  - GET: 리소스 조회
  - POST: 요청 내역 처리
<br></br>

### 요청 대상
- absolute-path[?query] (절대경로[?쿼리])
- 절대경로= "/"로 시작하는 경로
- 참고: http://...?x=y 와 같이 다른 유형의 경로지정 방법도 있다.
<br></br>

### 응답 메세지
- status-line = HTTP-version SP status-code SP reason-phrase CRLF
<br></br>

![20220520200519](https://user-images.githubusercontent.com/78770230/169515225-c043bf3c-fff1-4dd5-9e0f-d60bd2af6d93.jpg)
- HTTP 버전
- HTTP 상태 코드: 요청 성공, 실패를 나타냄
  - 200: 성공
  - 400: 클라이언트 요청 오류
  - 500: 서버 내부 오류
- 이유 문구: 사람이 이해할 수 있는 짧은 상태의 코드 설명 글
<br></br>

### HTTP 헤더
- header-field = field-name ":" OWS field-value OWS (OWS:띄어쓰기 허용)
- field-name은 대소문자 구문 없으나 value는 대소문자를 구분 한다.
<br></br>
- HTTP 전송에 필요한 모든 부가정보가 들어있다.
- 예) 메세지 바다의 내용, 메시지 바디의 크기, 압축, 인증, 요청 클라이언트(브라우저) 정보,  
  서버 애플리케이션 정보, 캐시 관리 정보...
- 표준 헤더가 너무 많음
  - https://en.wikipedia.org/wiki/ListofHTTPheaderfields
- 필요 시 임의의 헤더 추가 가능
  - helloworld: hihi
<br></br>
### HTTP 메세지 바디
- 실제 전송할 데이터가 들어있다.
- HTML 문서, 이미지, 영상, JSON 등등 byte로 표현할 수 있는 모든 데이터 전송 가능
- 압축해서 보낸다면 압축된 내용이 바디에 들어가게된다.
<br></br>

### 단순함 확장 가능
- HTTP는 단순하다. 스펙도 읽어볼만 하다...
- HTTP 메세지도 매우 단순하다.
- 크게 성공하는 표준 기술은 단순하지만 확장 가능한 기술이다.
<br></br><br></br>

출처 : 모든 개발자를 위한 HTTP 웹 기본 지식 : <https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC>,
