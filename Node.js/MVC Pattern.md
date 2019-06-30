# 	1. What is MVC Pattern?

### 	1) M Model 

=> Data

### 	2) V View

=> How does the data look

### 	3) C Control

=> Function that looks for the data, 어떤 일이 발생할지에 대한 일종의 로직

<br>

#### 대개 프로젝트에 존재하는 각 Model마다 Controller를 생성한다.

<br>

#### Router

```javascript
const VIDEO_DETAIL = "/:id";
const EDIT_VIDEO = "/:id/edit";
const DELETE_VIDEO = "/:id/delete";
```

Router가 똑똑해서 이렇게 url을 설정하면 id가 변하는 값임을 알아챈다.

Router와 Controller를 헷갈리지말자! (Router는 URL일 뿐!! 로직이 아니다.)

<br>

<br>

# 2. View

### app.set(name, value)

.set함수는 application을 설정하는 함수이다.

```javascript
app.set("view engine", "pug"); // 이 application의 view engine을 pug로 하겠다.
```

### 컨트롤러에 설정되어있는 send를 render로 바꿔준 후에 pug파일을 연결하면 된다.

```javascript
export const home = (req, res) => res.render("home");
export const search = (req, res) => res.send("Search");
// home과 search는 video에 관한 것이기에 videoController 파일에 입력했다.

export const videos = (req, res) => res.send("Videos");
export const upload = (req, res) => res.send("Upload");
export const videoDetail = (req, res) => res.send("Video Detail");
export const editVideo = (req, res) => res.send("Edit Video");
export const deleteVideo = (req, res) => res.send("Delete Video");
```

### Pug

Pug는 Express에서 View를 다루는 방식 중 하나이다. (일종의 View 엔진이다.) HTML이 멋지게 보이게 만들어준다. HTML과 CSS로만 작업할 경우, 반복되는 일을 너무 많이 하게돼 좋지않다. 단순작업을 하는 대신 pug를 사용하면 논리적으로 View를 관리할 수 있다.

(밑 코드는 pug코드이다.)

```html
doctype html
html <--! 탭안쪽에 있는 코드면, 그 내부에 있는 코드임을 뜻한다. -->
    head
        title Wetube
    body
        main
            block content <--! 실질적인 내용은 이안에 들어간다. 나머지 부분은 같고 이 main부분이 변경되어 각각의 화면 View에 적용된다. -->
        footer
            span &copy; Wetube
```

block content 이 부분에 다른 화면들의 내용들이 들어간다. (이게 main.pug)

밑에 코드는 main.pug를 extend한  home.pug이다.

```html
extends layouts/main <!-- main.pug를 그대로 가져오겠다.-->
	
block content
	p Hello <!-- block부분을 Hello p태그로 채우겠다.-->
```

### Partials

Pug는 document를 부분으로 나누어 레고 조립하듯이 사용할 수 있다.

```html
footer.footer
    .footer__icon
        i.fab.fa-youtube
    span.footer__text &copy; #{new Date().getFullYear()} Wetube
<!-- 이렇게 footer document를 만들고 이걸 다른 document footer에 사용가능하다. javascript를 pug에서 사용하고 싶으면 #{}안에 자바스크립트 코드를 작성하면 된다. -->
```

사용방법

```html
doctype html
html
    head
        link(rel="stylesheet", href="https://use.fontawesome.com/releases/v5.5.0/css/all.css", integrity="sha384-B4dIYHKNBt8Bc12p+WXckhzcICo0wtJAoU8YZTY5qE0Id1GSseTk6S+L3BlXeVIU", crossorigin="anonymous")
        title Wetube
    body
        header
            h1 Wetube
        main
            block content
        include ../partials/footer <!-- 이렇게 footer을 불러와서 main에 적용시킬 수 있다. -->
```

<br>

```html
.social-login
    button
        span
            i.fab.fa-github
        |Continue with Github
```

그냥 Continue with Github로 치면 Continue를 Tag로 인식한다. 그래서 앞에 |를 붙여 Continue with Github를 Text로 인식하게끔 만들어준다. (Pug 기능인 듯?)

<br>

### How to put javascript code in pug?

```pug
footer.footer
    .footer__icon
        i.fab.fa-youtube
    span.footer__text Wetube #{new Date().getFullYear()} &copy; 
```

<br>

### One Single Source of Truth

한곳에서만 정보를 보관. 코드를 더 좋게 만드는 원칙중 하나. 이 방식으로 코드를 짠다면 버그를 최소화 할 수 있다.

<br>

### Controller에 있는 정보를 Pug에 추가하는 방법

전역적으로(글로벌) 사용할 변수 추가방법 

local 변수를 global 변수로 사용할 수 있도록 만들어 주는 것.

```javascript
// middlewares.js 파일에 들어가는 코드
import routes from "./routes";

export const localsMiddleWare = (req, res, next) => {
    res.locals.siteName = "WeTube";
    res.locals.routes = routes;
    next(); // middleware 특징 다음 함수로 넘어가야됨.
};
// locals는 로컬 변수 응답을 포함하는 객체입니다. (다양한 변수를 설정할 수 있다.) res.locals로 시작하는 2줄 코드를 통해 routes와 siteName을 모든 템플릿, 뷰에서 사용할 수 있다.
```

middlewares.js 파일을 만들어  Controller정보를 활용할 수 있게한다.

```html
doctype html
html
    head
        link(rel="stylesheet", href="https://use.fontawesome.com/releases/v5.5.0/css/all.css", integrity="sha384-B4dIYHKNBt8Bc12p+WXckhzcICo0wtJAoU8YZTY5qE0Id1GSseTk6S+L3BlXeVIU", crossorigin="anonymous")
        title #{siteName} <!-- 위 코드 덕분에 이렇게 siteName을 pug에서 사용할 수 있게 되었다. -->
    body
        include ../partials/header
        main
            block content
        include ../partials/footer
```

<br>

### 템플릿마다 할당되는 변수를 다르게 설정하는 방법

위처럼 모든 템플릿에서 locals 변수에 접근하게도 할 수 있지만 특정 템플릿에서만 접근하게 하는 것도 가능하다.

```javascript
// videoController 코드 일부
export const home = (req, res) => res.render("home");
// view-engine을 pug로 설정해놓았기 때문에 render함수가 자동으로 views 폴더에서 home.pug을 찾는다.
```

render 함수의 첫 번째 인자는 템플릿이고 두 번째 인자는 추가할 정보가 담긴 객체이다.

```javascript
export const home = (req, res) => res.render("home", { pageTitle: "Home" });
```

이렇게 전달할 수 있다. 전달하고 싶은 것은 무엇이든 전달할 수 있다.

<br>

### BEM

CSS 방법론으로 html 요소에  클래스나 id를 설정할 때 특정한 규칙에 따라 설정하는 것을 말한다.

```html
<!-- join.pug -->
extends layouts/main

block content
    .form-container
        form(action=routes.join method="post")
            input(type="text", name="name" placeholder="Full Name")
            input(type="email" name="email" placeholder="Email")
            input(type="password" name="password" placeholder="Password")
            input(type="password", name="veriPassword", placeholder="Verify Password")
            input(type="submit" value="Join Now")
        include partials/socialLogin
```

```html
<!-- login.pug -->
extends layouts/main

block content
    .form-container
        form(action=routes.login method="post")
            input(type="email", name="email", placeholder="Email")
            input(type="password", name="password", placeholder="Password")
            input(type="submit", value="Login")
        include partials/socialLogin
```

```html
<!-- socialLogin.pug -->
.social-login
    button.social-login--github
        span
            i.fab.fa-github
        |Continue with Github
    button.social-login--facebook
        span
            i.fab.fa-facebook
        |Continue with Facebook
```

이 링크 참조

- [https://medium.com/witinweb/css-%EB%B0%A9%EB%B2%95%EB%A1%A0-1-bem-block-element-modifier-1c03034e65a1](https://medium.com/witinweb/css-방법론-1-bem-block-element-modifier-1c03034e65a1)

<br>

### Mixins

웹사이트에서 계속되어 반복되는 코드를 복사/붙혀넣기 하지 않고, 재활용하는 방법을 **`mixin`**이라한다. **`mixin`**은 pug 함수의 일종이다. 

```html
mixin videoBlock(video = {})
    .videoBlock
        video.videoBlock__thumbnail(src=video.videoFile, controls=true)
        h4.videoBlock__title= video.title
        h6.videoBlock__views= video.views
<!--이 코드의 의미는 mixin에 인자가 입력되면, 그 객체의 이름을 video라한다.-->
```

home.pug도 이에 맞게 수정한다.

```html
extends layouts/main
include mixins/videoBlock

block content
    .videos
        each item in videoList
            +videoBlock({
                videoFile: item.videoFile,
                title: item.title,
                views: item.views 
            })
<!-- 각각 다른 정보를 기지지만 같은 구조를 가진 데이터를 표시화기 위해 코드를 캡슐화 시킴. mixin을 사용하는 가장 큰 이유(다른 정보, 같은 구조) -->
```

<br>

<br>

# 3. Controller

### 컨트롤러도 query에 접근하려면 method가 get이어야 한다.

get method가 url에 정보를 추가해주기 때문이다.

<br>

### routes에서 주의할 사항

```javascript
// Global
const HOME = "/";
const JOIN = "/join";
const LOGIN = "/login";
const LOGOUT = "/logout";
const SEARCH = "/search";

// Users
const USERS = "/users";
const USER_DETAIL = "/:id";
const EDIT_PROFILE = "/edit-profile";
const CHANGE_PASSWORD = "/change-password";

// Videos
const VIDEOS = "/videos";
const UPLOAD = "/upload";
const VIDEO_DETAIL = "/:id";
const EDIT_VIDEO = "/:id/edit";
const DELETE_VIDEO = "/:id/delete";

const routes = {
    home: HOME,
    join: JOIN,
    login: LOGIN,
    logout: LOGOUT,
    search: SEARCH,
    users: USERS,
    userDetail: USER_DETAIL,
    editProfile: EDIT_PROFILE,
    changePassword: CHANGE_PASSWORD,
    videos: VIDEOS,
    upload: UPLOAD,
    videoDetail: VIDEO_DETAIL,
    editVideo: EDIT_VIDEO,
    deleteVideo: DELETE_VIDEO
};

export default routes;
```

```javascript
import express from "express";
import routes from "../routes";
import { users, userDetail, editProfile, changePassword } from "../controllers/userController";

const userRouter = express.Router();

userRouter.get(routes.users, users);
userRouter.get(routes.editProfile, editProfile);
userRouter.get(routes.userDetail, userDetail);
userRouter.get(routes.changePassword, changePassword);

export default userRouter;
```

여기서 /edit-profile url에 접근할 때,  이를 userDetail의 url인 /:id:로 인식할 수 있다. 그 이유는 router에서 userDetail이 editProfile보다 먼저 선언되어 있었기 때문이다. 브라우저가 /edit-profile을 /:id:로 인식하지 않게 하려면 router에서 editProfile을 먼저 선언해주면 된다.

<br>

### Search Controller

header.pug에 input 폼을 추가한다.

```html
header.header
    .header__column
        a(href=routes.home)
            i.fab.fa-youtube
    .header__column
        form(action=routes.search, method="get")
            input(type="text", placeholder= "Search By Term", name="term")
<!-- name을 설정해야 url에 표시가 된다., 컨트롤러가 쿼리에 접근하려면 method가 get이어야 한다. 왜냐하면 get 방식이 url에 정보를 추가하기 때문이다.-->
    .header__column
        ul  
            li
                a(href=routes.join) Join
            li
                a(href=routes.login) Log In
```

search.pug도 들어온 input값을 반영할 수 있도록 수정한다.

```html
extends layouts/main

block content
    .search__header 
        h3 Searching By #{searchingBy}
```

아직 searchingBy 변수에 값을 넣지 않아서 화면에 이를 반영할 수 없다. 따라서 컨트롤러를 수정해 searchingBy값을 설정하도록 한다.

videoController로 가서 Search Controller를 수정한다.

```javascript
export const search = (req, res) => {
  //const searchingBy = req.query.term;
  const {
    query: { term: searchingBy }
  } = req;
  // es6에서는 이렇게 값을 설정해서 변수에 할당할 수 있다.
  res.render("search", { pageTitle: "Search", searchingBy });
};
```

<br>

### Home Controller

가짜 데이터베이스를 생성하고 이를 Home화면에 적용하는 코드.

1. db.js를 작성

```javascript
export const videoList = [
  {
    id: 324393,
    title: "Video awesome",
    description: "This is something I love",
    views: 24,
    videoFile: "https://archive.org/details/BigBuckBunny_124",
    creator: {
      id: 121212,
      name: "Nicolas",
      email: "nico@las.com"
    }
  },
  {
    id: 1212121,
    title: "Video super",
    description: "This is something I love",
    views: 24,
    videoFile: "https://archive.org/details/BigBuckBunny_124",
    creator: {
      id: 121212,
      name: "Nicolas",
      email: "nico@las.com"
    }
  },
  {
    id: 55555,
    title: "Video nice",
    description: "This is something I love",
    views: 24,
    videoFile: "https://archive.org/details/BigBuckBunny_124",
    creator: {
      id: 121212,
      name: "Nicolas",
      email: "nico@las.com"
    }
  },
  {
    id: 11111,
    title: "Video perfect",
    description: "This is something I love",
    views: 24,
    videoFile: "https://archive.org/details/BigBuckBunny_124",
    creator: {
      id: 121212,
      name: "Nicolas",
      email: "nico@las.com"
    }
  }
];
```

2. videoController.js에서 db.js로부터 videoList를 받아와 home 화면  렌더링할 때 videosList 보내기

```javascript
import { videoList } from "../db";

export const home = (req, res) => {
  res.render("home", { pageTitle: "Home", videoList });
};
```

3. home.pug에서 받아온 videoList를 받아와 화면에 뿌리기

```html
extends layouts/main

block content
    .videos
        each item in videoList <!--이 each 코드 기억하고 있기-->
            h1= item.title
            p= item.description
```

<br>

### 로그인 상태에 따라 header.pug 화면 바꾸기

```html
header.header
    .header__column
        a(href=routes.home)
            i.fab.fa-youtube
    .header__column
        form(action=routes.search, method="get")
            input(type="text", placeholder= "Search By Term....", name="term")
    .header__column
        ul 
            if !user.isAuthenticated
                li
                    a(href=routes.join) Join
                li
                    a(href=routes.login) Log In
            else 
                li
                    a(href=routes.upload) Upload
                li
                    a(href=routes.userDetail(user.id)) Profile
                li
                    a(href=routes.logout) Log Out
```

user라는 가짜 데이터를 집어넣고 동작하는지를 본다. (데이터는 Middleware에서 locals로 넣는다.)

```javascript
import routes from "./routes";

export const localsMiddleware = (req, res, next) => {
    res.locals.siteName = "Wetube";
    res.locals.routes = routes;
    res.locals.user = {
        isAuthenticated: true,
        id: 1
    };
    next();
};
```

이렇게 하면 `isAuthenticated` 값을 바꿈으로서 header 파일을 제어할 수 있다. (실제 데이터를 통해 로그인 되었을때는 true이고 아니면 false를 전달.) 그 다음 id 데이터를 통해 user 정보화면 나타낼 수 있다.

```javascript
const routes = {
    home: HOME,
    join: JOIN,
    login: LOGIN,
    logout: LOGOUT,
    search: SEARCH,
    users: USERS,
    userDetail: id => {
        if (id) {
            return `/users/${id}`;
        } else {
            return USER_DETAIL;
        }
    },
    editProfile: EDIT_PROFILE,
    changePassword: CHANGE_PASSWORD,
    videos: VIDEOS,
    upload: UPLOAD,
    videoDetail: id => {
        if (id) {
            return `/videos/${id}`;
        } else {
            return VIDEO_DETAIL;
        }
    },
    editVideo: EDIT_VIDEO,
    deleteVideo: DELETE_VIDEO
};
```

 `routes.js` 파일에서 routes 값을 id인자에 따라 변하는 함수를 줌으로써 id에 따라 User 화면이 바뀌는 것을 구현. (Video도 마찬가지)

```javascript
import express from "express";
import routes from "../routes";
import {
    users,
    userDetail,
    editProfile,
    changePassword
} from "../controllers/userController";

const userRouter = express.Router();

userRouter.get(routes.users, users);
userRouter.get(routes.editProfile, editProfile);
userRouter.get(routes.changePassword, changePassword);
userRouter.get(routes.userDetail(), userDetail);

export default userRouter;
```

`routes.userDetail`을 `routes.userDetail()`로 바꿔준다. (함수로 바꾸었기 때문에.) 

<br>

<br>

# 4. Model

#### 실제 데이터베이스와 연동하기 전에 가짜 데이터베이스를 만들어서 적용시켜보는 것은 좋은 방법이다.

<br>

### MongoDB

많은 데이터베이스들이 존재하는데, 크게 SQL과 NoSQL로 구분된다. 

MongoDB는 NoSQL 기반이며 더 적은 규칙과 절차로 작업이 가능한 데이터베이스이다. 

(예를 들어, 실시간 채팅을 만드는데 있어 MongoDB는 적합한 DataBase라 할 수 있다.)

MongfoDB를 설치한 후에는 MongoDB를 JavaScript와 연결하는데 이를 위해서는 Adapter를 통해야 한다. 이것을 실행해주는 Adapter가 바로 Mongoose이다. 

<br>

### Mongoose

Mongoose는 NodeJS를 위한 Object Modeling이다. 

```powershell
PS C:\Users\user\Desktop\revieWetube> npm install mongoose
```

MongoDB와 Mongoose를 설치한 후에는, db.js에 저장되어있는 가짜 데이터베이스를 지우고 MongoDB와 연결한다.

<br>

### Dotenv

```powershell
PS C:\Users\user\Desktop\revieWetube> npm install dotenv
```

dotenv는 어떤부분을 숨기고 싶을 때 사용한다. (예를 들어, Open Source 프로젝트를 하고 있을 때, 데이터베이스를 숨기고 싶은 경우.)

dotenv 설정

1. 프로젝트 폴더 밑에 `.env` 파일 생성

```
MONGO_URL="mongodb://localhost:27017/wetube"
PORT=3000
```

2.  `db.js`에 아래와 같이 코드 입력

```javascript
import mongoose from "mongoose";
import dotenv from "dotenv";
dotenv.config();

mongoose.connect(process.env.MONGO_URL, {
  useNewUrlParser: true,
  useFindAndModify: false
});

const db = mongoose.connection;

const handleOpen = () => console.log("✅ Connected to DB");
const handleError = err => console.log(`❌ Error on DB Connection: ${err}`);

db.once("open", handleOpen);
db.on("error", handleError);
```

3. `init.js`에도 코드 입력

```javascript
import "./db";
import app from "./app";
import dotenv from "dotenv";
dotenv.config();

const PORT = process.env.PORT || 3000;

const handleListening = () =>
  console.log(`✅ Listening on port: http://localhost:${PORT}`);

app.listen(PORT, handleListening);
```

4. 이후,  `.gitignore` 파일에 .env를 파일을 추가. (.gitignore 파일을 생성하면 .env 파일이 이미 추가되어있음. 혹시 없다면 .env 파일을 추가하여 github에서 .env파일을 확인할 수 없게 한다.)

위 작업을 통해 내 데이터베이스 URL을 숨길 수 있다.

<br>

<br>

# 5. 통신 상태

### Status Code

상태 코드란, 인터넷이 어떻게 상호작용하는지 표시하는 것을  의미한다.

많은 상태코그가 존재하고 브라우저는 이를 인식할 수 있다.

https://developer.mozilla.org/ko/docs/Web/HTTP/Status

**위 링크 참조**

```javascript
// userController 코드
export const postJoin = (req, res) => {
  // console.log(req.body);
  const {
    body: { name, email, password, veriPassword }
  } = req;

  if (password !== veriPassword) {
    res.status(400);
    res.render("join", { pageTitle: "Join" });
  } else {
    //Todo: Register user
    //Todo: Log user in
    res.redirect(routes.home);
  }
};
//이렇게 error status를 담아서 에러를 전달하는 방법이 있다.
```

