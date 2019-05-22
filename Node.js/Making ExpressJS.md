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

