# 1. What is Server?

Server란 컴퓨터다. 인터넷에 연결된 컴퓨터.

#### 소프트웨어적 서버 => 인터넷에 연결된 한 덩어리의 코드





# 2. What is Express.JS?

##### Node.js 프레임워크(몇 줄 코드 입력으로 서버를 만들 수 있다.)

##### 프레임워크 => 이미 완성되어있는 형태로서 원하는걸 더 빨리 만들 수 있게하는 장치

##### 매우 안정적임(완성도가 높아 버전업이 많지가 않다.)





# 3. What is npm?

Node Package Manager의 줄임말로 어떤 파일이나 변경사항이 있을때 서버도 변경해야하는 <br>번거로움을 해결해주는 일종의 패키지월드(모든 node.js관련 패키지가 모여있는 node.js 월드라 생각하면 됨.)

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

### 	1. GET

url을 브라우저에 입력하면 브라우저가 GET method를 실행한다. 이러한 방식으로 브라우저는 웹페이지를 읽어온다. GET request는 그에 대한 응답이 있어야한다.  request object, response object는 매우 다른 것이다.

### 	2. POST

웹사이트에 로그인을 할 시에는 POST를 통하게 된다. 브라우저가 POST라는 method를 통해 웹사이트에 정보를 전달하는 것이라 이해하면 됨.

=>  이것이 결과론적으로 http가 작동하는 방식!!





# 5. What is Babel?

### 	Babel

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
	console.log("Hi");
}
```

이 코드를

```javascript
const handleListening = () => console.log("Hi");
```

이렇게 표현할 수 있고 밑에 형식을 Arrow Function이라 칭한다.





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

### dependency란 프로젝트가 실행될 때 필요한 것을 말한다.

만약에 dependency에 포함되지 않는 (상관없는? 프로젝트를 실행하는데 필요한게 아닌)  것을 설치하고 싶다면 뒤에 -D를 추가하면 된다. 

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