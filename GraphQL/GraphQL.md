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

<br>

### Creating a GraphQL Server with GraphQL Yoga

GraphQL Server 생성

index.js

```javascript
import { GraphQLServer } from "graphql-yoga";

const server = new GraphQLServer({});

server.start(() => console.log("GraphQL Server Learning"));
```

이렇게만 작성하고 서버를 돌리면 Schema가 없다는 에러가 발생한다. (Schema는 사용자에게 보내거나 사용자로부터 받을 data에 대한 설명이다.)

<br>

### Creating the first Query and Resolver

위에 언급한 것처럼 Schema는 Data에 대한 일종의 서술이라 생각하면 된다.ㄴ

**Schema 작성**

프로젝트에 graphql 폴더를 만들고 그 안에 schema.graphql 파일을 생성하자.

```
type Query{
    name: String!
}
```

GraphQl에서 Query는 정보를 가져올 때만 사용되며, 데이터를 바꾸는 것은 Mutaion이라 한다.

index.js 수정

```javascript
import { GraphQLServer } from "graphql-yoga";

const server = new GraphQLServer({
  typeDefs: "graphql/schema.graphql"
});

server.start(() => console.log("GraphQL Server Learning"));
```

이렇게까지만 코드를 작성하면 Query에 이름을 보내면 string을 보낸다는 설명만 했을 뿐이다. 따라서 코드를 동작하게 만들기 위해서, Resolvers를 만들어야 한다. Resolvers란, Query를 resolve(해결) 한다는 의미이다. (Query는 Database에게 있어 문제 같은 것이고, 따라서 이 Query를 resolve(해결)해야 한다.)

graphql 폴더 밑에 resolvers.js 파일 생성

```javascript
const resolvers = {
  Query: {
    name: () => "Park Choong Ho"
  }
};

export default resolvers;
```

index.js 수정

```javascript
import { GraphQLServer } from "graphql-yoga";
import resolvers from "./graphql/resolvers";

const server = new GraphQLServer({
  typeDefs: "graphql/schema.graphql",
  resolvers
});

server.start(() => console.log("GraphQL Server Running"));
```

<br>

