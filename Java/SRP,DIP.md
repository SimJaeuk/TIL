## SRP(Single Responsibility Principle) - 단일 책임 원칙

### `한 클래스는 하나의 책임만 가져야 한다.`

![20220128013812](https://user-images.githubusercontent.com/78770230/151404715-538bbe84-e786-4c37-a4a7-95afd743ba8d.jpg)

- 작성된 클래스는 하나의 기능만 가지며 클래스가 제공하는 모든 서비스는 그 하나의 책임을 수행하는데 집중되어 있어야 함
- 이는 객체지향 원리의 대전제 격인 OCP원리 뿐만 아니라 다른 원리들을 적용하는 기초가 됨
- 책임만 분리하는것이 아닌 두 클래스간의 관계 복잡도를 줄이도록 설계

### 효과

- 책임 영역이 확실해 짐으로 잘못된 연쇄작용에서 자유로울 수 있음
- 책임을 적절히 분배함으로 코드의 가독성을 향상하고 유지보수를 용이하게 함


## DIP(Dependency inversion principle) - 의존관계 역전 원칙

### `프로그래머는 구체화에 의존하는것이 아닌 추상화에 의존해야한다.`

![20220128014633](https://user-images.githubusercontent.com/78770230/151404735-9ffefca0-c3fd-4001-93c0-a78aad536b78.jpg)

- 하위 레벨 모듈의 변경이 상위 레벨 모듈의 변경을 요구하는 위계 관계를 끊는 의미의 역전
- 실제 사용 관계는 바뀌지 않으며, 추상을 매개로 메세지를 주고 받음으로써 관계를 최대한 느슨하게 만드는 원칙
- 상위 레벨의 레이어가 하위 레벨의 레이어를 바로 의존하게 하는 것이 아니라 둘 사이에 존재하는 추상레벨을 통해 의존 해야함
- 키워드는 IOC, Hook Method, 확장성


### 효과

- 복잡한 컴포넌트들의 관계를 단순화하고 컴포넌트 간의 커뮤니케이션을 효율적이게 함

#### 출처 : 
데어 프로그래밍 JAVA강의 <https://www.easyupclass.com/course/274/about>,  
Keep Going벨로그 <https://velog.io/@hanblueblue/Java-SOLID-SRP-OCP-LSP-ISP-DIP>
