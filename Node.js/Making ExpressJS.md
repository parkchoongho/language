# 1. What is Server?

Server란 컴퓨터다. 인터넷에 연결된 컴퓨터.

#### 소프트웨어적 서버 => 인터넷에 연결된 한 덩어리의 코드





# 2. What is Express.JS?

##### Node.js 프레임워크(몇 줄 코드 입력으로 서버를 만들 수 있다.)

##### 프레임워크 => 이미 완성되어있는 형태로서 원하는걸 더 빨리 만들 수 있게하는 장치

##### 매우 안정적임(완성도가 높아 버전업이 많지가 않다.)







# 3. What is npm?

Node Package Manager의 줄임말로 어떤 파일이나 변경사항이 있을때 서버도 변경해야 하는 번거로움을 <br>해결해주는 일종의 패키지모음(Node.js관련 패키지가 모두 모여있는 Node.js 패키지 총 집합이라 생각하면 됨.)

npm을 실행할 때는 반드시 package.json 파일이 있는 폴더에서 명령을 내려야 한다.



### npm 설치 코드

```shell
PS C:\Users\user\Desktop\Project\wetube> ls
PS C:\Users\user\Desktop\Project\wetube> node .\index.js
Hi!
PS C:\Users\user\Desktop\Project\wetube> npm -v
6.4.1
PS C:\Users\user\Desktop\Project\wetube> npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (wetube)
version: (1.0.0)
description: Cloning Youtube with Vanilla and NodeJS
entry point: (index.js)
test command:
git repository:
keywords:
author: Park Choong Ho
license: (ISC)
About to write to C:\Users\user\Desktop\Project\wetube\package.json:

{
  "name": "wetube",
  "version": "1.0.0",
  "description": "Cloning Youtube with Vanilla and NodeJS",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Park Choong Ho",
  "license": "ISC"
}


Is this OK? (yes) y
PS C:\Users\user\Desktop\Project\wetube> npm install express
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN wetube@1.0.0 No repository field.

+ express@4.17.0
added 50 packages from 37 contributors and audited 126 packages in 18.158s
found 0 vulnerabilities
```





# 4. Handling Routes with Express



### 		1. GET

url을 브라우저에 입력하면 브라우저가 GET method를 실행한다. 이러한 방식으로 브라우저는 웹페이지를 읽어온다. GET request는 그에 상응하는 GET response가 있어야 한다.  그래야만 request가 종료된다.



### 		2. POST

브라우저가 POST라는 method를 통해 웹사이트에 정보를 전달하는 것이라 이해하면 됨. 

예를 들어, 웹사이트에 로그인을 할 시에 POST를 통하게 된다.

=>  이것이 http가 작동하는 방식!!



### 	MiddleWare

처리가 끝날때까지 연결되어 있는 함수.



#### 	연결이 동작하는 방식

시작은 브라우저에서 웹사이트에 접속하려 하면 연결이 동작하기 시작.

웹사이트에 접속하면  그에 해당하는 JS파일을 실행하고 route가 존재하는지 살핀다. 그리고 그 route에 존재하는<br>함수를 실행하고 그 함수에 적혀있는 코드를 실행하는 구조.

=> But, 응답은 쉽게 이루어지지 않는다. 중간 연결자가 존재. (더 자세히는 유저와 응답사이에 존재)

이걸 **MiddleWare**라 칭한다. 따라서 MiddleWare를 기준으로 계층을 형성할 수 있다. (이 사이트에 로그인 하는 유저의 상태를 확인한다거나 권한을 확인하는 등등에 활용)



#### 	Express에서의 모든함수는 MiddleWare가 될 수 있다.

```javascript
const betweenHome = () => console.log("I'm between!");

app.get("/", betweenHome, handleHome);
```

위처럼 코드를 작성하고 브라우저에 주소를 입력하면 계속 로딩되는 상태에서 다음으로 넘어가지 않는다.



#### 	Expreess에서 route를 포함한 모든 connection을 다루는 것들은 req, res, next를 가지고 있다. 

```javascript
const betweenHome = (req, res, next) => {
    console.log("Between!");
    next();
};

app.get("/", betweenHome, handleHome);
```

위처럼 바꿔주면 다시 handleHome함수를 실행한다.

만일 모든 route에 대하여 Middleware을 실행하고 싶다면 이렇게 입력하면 된다.

```javascript
app.use(betweenHome);

app.get("/", handleHome);

app.get("/profile", handleProfile);
```

이렇게 코드를 짜면 "/", "/profile" route 모두 betweenHome함수를 MiddleWare로 사용한다. (이렇게 코드를 짜는 걸 전역적이라한다.)

=> 만일 app.use(betweenHome) 이 코드를 profile route 뒤에 두면 2개 route 모두에서 betweenHome MiddleWare가 실행이 안된다. 코드는 위에서 부터 아래로 실행되므로 순서를 항상 염두에 두고 있자.



### Morgan 

Logging에 도움을 주는 MiddleWare

Logging은 기본적으로 무슨일이 언제 일어났는지 기록하는 것.

```javascript
import morgan from "morgan";
app.use(morgan("tiny"));
```

이렇게 사용 가능. "tiny"를 대신해 다른 옵션들이 들어갈 수있다.



### Helmet

NodeJS의 보안에 도움을 주는 MiddleWare이다.

```javascript
import helmet from "helmet";
app.use(helmet());
```

위 코드를 추가해주면 된다. (Morgan에서 Helmet으로 바뀐것 빼고 코드가 똑같다.)



### Cookie Parser, Body Parser

Cookie와 Body를 다룰 수 있게 도와주는 MiddleWare.

**Body Parser**

사용자가 웹사이트로 전달하는 정보를 검사하는 미들웨어

누군가 form을 채워 넣고 나에게 전송한다면 그 form은 서버에 의해서 받아져야한다. (서버를 거쳐야 한다는 뜻 같다.)

ex) 만약 아이디와 비밀번호를 입력했다면 특정 형태로 변환 후 서버에게 전송된다.

만약 form을 받았다면 그 데이터는 request object가 가지고 있다. 또 서버에서 request object에 접근할 수 있어야 한다. 

=> Body Parser에는 많은 옵션이 존재. 

```javascript
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({extended:true}));
/* 이것은 서버에 넘어오는 파일중 json 데이터와 form 형식에서 오는 데이터를 서버가 이해하기 위해 작성하는 코드이다. */
```

이것에 있어 필요한 것이 Body Parser

**Cookie Parser**

Cookie에 유저정보를 저장하고 Session을 다루기 위해서 사용.

사용 방식은 둘 다 Helmet MiddleWare와 똑같다.





### MiddleWare제어를 통해 통신을 끊을 수 있다. => 기억하고 있을 것.



```javascript
const middleware = (req, res, next) => {
    res.send("Not Happening");
}

app.get("/", middleware, handleHome);
```

이렇게 사용 가능



# 5. What is Babel?

### 		Babel

Babel은 자바스크립트 컴파일러로 최신의 자바스크립트를 무난한 예전의 자바스크립트로 변환시켜준다. <br>Babel Node란 NodeJS에서 Babel을 사용하는 것이다.

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install @babel/node
```

Babel을 설치하고 .babelrc 파일을 만든 후, 밑에 코드를 추가한다.

```json
{
  "presets": ["@babel/preset-env"]
}
```





# 6. ES6

​	ES6은 가장 최근 형태의 자바스크립트이며 몇가지 특징을 가진다.	

### 1) Arrow Function	

```javascript
function handleListening (){
	return true;
}
```

이 코드를

```javascript
const handleListening = () => true;
```

이렇게 표현할 수 있고 밑에 형식을 Arrow Function이라 칭한다.

Arrow Function에는 Implicit Return(암시적 리턴)이라는 것이 있다. 만일 대괄호를 적는다면 암시적 성격을 잃게 되며 그 때는 return을 적어야 한다.

```javascript
const handleListening = () => {
    return true;
}
```



### 2) Module

ES6에는 Module이 존재해서 코드를 공유할  수 있다. 다른 파일에 있는 코드를 가져다가 쓸 수 있다.

```javascript
export default app;
```

=> 이 말은 만일 다른 파일에서 이 파일을 부른다면 app object를 준다는 말이다.

이러면 같은 폴더에 위치한 파일에서는 이렇게 불러올 수 있다.

```javascript
import app from "./app";
```

만약에 default로 export하지 않았다면 

```javascript
import { app } from "./app";
```

### Default로 Export한 것과 아닌것의 차이점은 무엇일까?

Default로 export한것은 파일채로 export하는 것이다.





# 7. Dependency

package.json 파일을 보면 "dependencies" 키값이 존재한다.

```json
{
  "name": "wetube",
  "version": "1.0.0",
  "description": "Cloning Youtube with Vanilla and NodeJS",
  "author": "Park Choong Ho",
  "license": "ISC",
  "dependencies": {
    "@babel/core": "^7.4.5",
    "@babel/node": "^7.4.5",
    "@babel/preset-env": "^7.4.5",
    "express": "^4.17.0"
  },
  "scripts": {
    "start": "babel-node index.js"
  }
}
```

### 	dependency란 프로젝트가 실행될 때 필요한 것을 말한다.

만약에 dependency에 포함되지 않는 (프로젝트를 실행하는데 필요한게 아닌)  것을 설치하고 싶다면 뒤에 -D를 추가하면 된다. 

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install nodemon -D
```

이렇게 입력하고 나면 package.json 파일에 이러한 것이 추가 된다.

```javascript
{
  "devDependencies": {
    "nodemon": "^1.19.0"
  }
}
```

 devDependencies의 의미는 이것은 개발자에게 필요한 것이지, 프로젝트에 필요한 것이 아니라는 의미이다.

nodemon은 서버를 죽이지않고 내 코드의 변경사항을 반영할 수 있게 해준다. (내 코드를 저장하면 변경사항을 파악해 이를 반영한 서버를 다시 실행한다.)





# 8. Router

Route의 복잡함을 쪼개는데 활용되는 것. 

=> 많은 Route들이 담겨있는 파일이 Router다.

app.js

```javascript
import express from "express"; //import express
import morgan from "morgan";
import helmet from "helmet";
import cookieParser from "cookie-parser";
import bodyParser from "body-parser";
import { userRouter } from "./router";

const app = express(); // call express

const handleHome = (req, res) => res.send("Hello from home");

const handleProfile = (req, res) => res.send("You are on my profile.");
/*
const betweenHome = (req, res, next) => {
    console.log("Between!");
    next();
};

app.use(betweenHome);
*/

app.use(cookieParser());
app.use(bodyParser.json());
app.use(bodyParser.urlencoded());
app.use(helmet());
app.use(morgan("dev"));

app.get("/", handleHome);

app.get("/profile", handleProfile);

app.use("/user", userRouter);

export default app;
```

route.js 

```javascript
import express from "express";

export const userRouter = express.Router();

userRouter.get("/", (req, res) => res.send("user index"))
userRouter.get("/edit", (req, res) => res.send("user edit"))
userRouter.get("/password", (req, res) => res.send("user password"))
```

