# GraphQL

### Hello and Introduction

GraphQL 프로젝트 설정

```powershell
PS C:\Users\user\Desktop\Project\graphQL_movie> yarn init
```

graphql-yoga 설치

```powershell
PS C:\Users\user\Desktop\Project\graphQL_movie> yarn add graphql-yoga
```

graphql-yoga는 create-react-app이랑 비슷한 명령어로 Graphql 프로젝트를 빠르게 실행할 수 있게 도와준다. (완전한 기능을 갖춘 GraphQL 서버라 생각하면 된다.)

<br>

### Problems solved by GraphQL

GraphQL로 크게 Over-fetching와 Under-fetching 두가지 문데를 해결할 수 있다. 

예를 들어, 웹사이트에서 사용자 전체 해당하는 목록을 보여준다고 하면 users에서는 사용자 명 뿐만 아니라, 성별이나 프로필 사진 같은 정보들도 전달할 것이다. 근데 처음 리스트에서는 이름만 보여주고 나중에 이러한 정보들을 가져오고 싶다면, URL을 2번 호출해야 한다. 이렇게 Database에서 내가 사용하지 않는 부분을 요청하는 방식은 비효울적이다. 

=> 이것이 Over-fetching이다. 필요한 영역의 정보보다, 많은 정보를 서버에서 받는 것.

Under-fetching은 어떤 하나를 완성하기 위해, 다른 요청이 필요한 상황. 예를 들어, 앱이 처음 동작하는데 알림, 피드, 유저 정보 등 3가지 요청이 필요한 경우를 Under-fetching이라고 한다. 

=> REST에서 한가지를 완성하려고 여러가지 소스를 요청하는 것.

GraphQL을 사용하면, 하나의 query로 정확하게 원하는 정보만을 받을 수 있다.

**그렇다면, GraphQL에서는 어떻게 내가 원하는 여러정보만을 받아올 수 있을까?**

GraphQL에서는 URL이 존재하지 않는다. 오직 하나의 종점만이 존재. GraphQL을 활용하면 요청한 정보들만 원하는 방식으로 가져오거나 변형할 수 있다.