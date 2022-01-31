# Object 클래스

### `모든 자바 클래스의 최상위 조상 클래스`

## 오브젝트
- new 가능한 대상

![20220131231509](https://user-images.githubusercontent.com/78770230/151809264-fc42afa2-427d-4010-ae16-6a5b60e724e4.jpg)
(필드없이 11개의 메소드로 구성)
![20220131231509](https://user-images.githubusercontent.com/78770230/151810387-0ea2bef0-99c3-4a9d-8f57-1b8dc1633442.jpg)

- 모든 클래스는 Object 클래스에서 상속을 받는다.
- 따라서 Object클래스의 다양한 메소드를 어떤 클래스에서도 호출할 수 있다.



## 대표적인 Object 메소드
- equals() 메소드 : 두 객체가 동일한 객체라면 true를 리턴하고, 다르다면 false를 리턴
- hashCode() 메소드 : 객체의 메모리 번지를 이용해서 해시코드를 만들어 리턴 (객체마다 다른값을 가지고 있음)
- toString() 메소드 : 객체의 문자 정보를 리턴 (객체를 문자열로 표현)

#### 출처 : 
데어 프로그래밍 JAVA강의 <https://www.easyupclass.com/course/274/about>,  
TCPSCHOOL <http://www.tcpschool.com/java/java_api_object>
