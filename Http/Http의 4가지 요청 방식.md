# Http의 4가지 요청 방식

![20220209181931](https://user-images.githubusercontent.com/78770230/153164586-05b6bad8-ec84-4c6f-9ae3-ff5e5a401673.jpg)


## 1.GET(조회)
- 데이터를 읽을 때 사용된다.
- 같은 요청을 여러 번 하더라도 항상 같은 응답을 받을 수 있다.
- DB로 생각했을 때 SELECT에 해당

<br></br>

## 2.POST(등록)
- 서버에게 resource를 보내면서 생성해 달라고 요청한다.
- 같은 요청을 여러 번 할때 항상 같은 결과물이 나오는 것을 보장하지 않는다.
- DB로 생각했을 때 INSERT에 해당

<br></br>

## 3.PUT(수정)
- 서버에게 resource를 업데이트 하거나 없다면 새로운 resource를 생성해 달라고 요청한다.
- 동일한 요청을 여러 번 호출해도 항상 동일한 결과가 생성된다.
- DB로 생각했을 때 UPDATE에 해당

<br></br>

## 4.DELETE(삭제)
- 서버에게 resource의 삭제를 요청한다.
- DB로 생각했을 때 DELETE에 해당
<br></br><br></br>


출처 : 메타코딩 : <https://www.easyupclass.com/course/218/about>,  
MemoStack  :  <https://memostack.tistory.com/180>


