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

```jade
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

```jade
extends layouts/main <!-- main.pug를 그대로 가져오겠다.-->
	
block content
	p Hello <!-- block부분을 Hello p태그로 채우겠다.-->
```

### Partials

Pug는 document를 부분으로 나누어 레고 조립하듯이 사용할 수 있다.

```jade
footer.footer
    .footer__icon
        i.fab.fa-youtube
    span.footer__text &copy; #{new Date().getFullYear()} Wetube
<!-- 이렇게 footer document를 만들고 이걸 다른 document footer에 사용가능하다. javascript를 pug에서 사용하고 싶으면 #{}안에 자바스크립트 코드를 작성하면 된다. -->
```

사용방법

```jade
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

```jade
.social-login
    button
        span
            i.fab.fa-github
        |Continue with Github
```

그냥 Continue with Github로 치면 Continue를 Tag로 인식한다. 그래서 앞에 |를 붙여 Continue with Github를 Text로 인식하게끔 만들어준다. (Pug 기능인 듯?)

<br>

### How to put javascript code in pug?

```jade
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

```jade
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

```jade
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

```jade
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

```jade
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

```jade
header.header
    .header__column
        a(href=routes.home)
            i.fab.fa-youtube
    .header__column
        form(action=routes.search, method="get")
            input(type="text", placeholder= "Search By Term", name="term")

    .header__column
        ul  
            li
                a(href=routes.join) Join
            li
                a(href=routes.login) Log In
```

name을 설정해야 url에 표시가 된다. 그리고 컨트롤러가 쿼리에 접근하기 위해서는 method가 get이어야 한다. 왜냐하면 get 방식이 url에 정보를 추가하기 때문이다.

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

### Model 생성

MongoDB의 장점은 document를 줄여준다는 것이다. document의 대표적인 예는 JSON 파일이 있다. MongoDB에 Model이 어떻게 구성되는지 알려주어야 한다.

models라는 폴더를 생성하고 그 밑에 Video.js(Model 파일임을 알기 위해 첫 글자를 대문자로 한다.) 파일을 생성한다.

```javascript
import mongoose from "mongoose";
// model은 document 이름이자 실제 data이고 schema는 형태를 의미한다.

const VideoSchema = new mongoose.Schema({
  fileUrl: {
    // 영상 파일 자체를 Database에 저장하면 너무 무거워지므로 Url을 참조하는 방식을 사용. 영상의 주소를 저장.
    type: String,
    required: "File URL is required" // fileUrl 값이 없으면 이 "File URL is required"를 값으로 취한다.
  },
  title: {
    type: String,
    required: "Title is required"
  },
  description: String, // configuration이 필요하면 (다른 옵션을 줘야하면 object로 생성) 위 처럼 객체로 작성하고 필요 없으면 이렇게 한줄로 작성. 
  views: {
    type: Number,
    default: 0
  },
  createdAt: {
    type: Date,
    default: Date.now
  }
});

// 위에서 작성한 Schema를 통해 Model 작성

const model = mongoose.model("Video", VideoSchema);
export default model;
// 여기까지 작성하면 Database와 연결은 되어있지만 거기에 model이 있다는 것은 DB가 인지 못하는 상태.
```

mongoose documentation schema section에서 모든 option을 확인가능하다.

위 코드를 완성한 후 init.js에 아래 코드를 추가해 Database가 model이 있다는 것을 인지할 수 있게한다.

```javascript
import "./models/Video";
```

<br>

### Data Relationship

Data간의 관계를 설정하는 것은 매우 중요한 작업이다. (예를 들어, Video에 Comment를 달때, Comment Model과 Video Model을 어떻게 연관시킬 것인가)

=> 크게 2가지 방법이 있다.

1. Comment 모델은 그대로 두고 Video 모델에 해당 비디오에 소속되어 있는 Comment ID가 담긴 array를 추가하는 방법.

```javascript
import mongoose from "mongoose";
// model은 document 이름이자 실제 data이고 schema는 형태를 의미한다.

const VideoSchema = new mongoose.Schema({
  fileUrl: {
    // 영상 파일 자체를 Database에 저장하면 너무 무거워지므로 Url을 참조하는 방식을 사용. 영상의 주소를 저장.
    type: String,
    required: "File URL is required" // fileUrl 값이 없으면 이 "File URL is required"를 값으로 취한다.
  },
  title: {
    type: String,
    required: "Title is required"
  },
  description: String,
  views: {
    type: Number,
    default: 0
  },
  createdAt: {
    type: Date,
    default: Date.now
  },
  comments: [{ type: mongoose.Schema.Types.ObjectId, ref: "Comment" }]
});

// 위에서 작성한 Schema를 통해 Model 작성

const model = mongoose.model("Video", VideoSchema);
export default model;
// 여기까지 작성하면 Database와 연결은 되어있지만 거기에 model이 있다는 것은 DB가 인지 못하는 상태.
```

2. Commet 모델에 해당 Video에 아이디를 주는 방법.

```javascript
import mongoose from "mongoose";

const commentSchema = new mongoose.Schema({
  text: {
    type: String,
    required: "Text is required"
  },
  createdAt: {
    type: Date,
    default: Date.now
  },
  video: {
    type: mongoose.Schema.Types.ObjectId,
    ref: "Video"
  }
});

const model = mongoose.model("Comment", commentSchema);

export default model;
```

둘다 각각에 연결된 모델 객체의 ID만을 저장한다. (수업에서는 첫 번째 방법을 사용)

<br>

### 컨트롤러에 연결하기

컨트롤러에 모델을 연결하기 위해 아래의 코드 videoController 파일에 추가

```javascript
import Video from "../models/Video" 
// 모델을 연결한 것이지, Database의 요소를 연결한 것 아니다. (요소를 받는 통로이지, 요소 자체가 아니다.)=> 꼭 기억할것. 중요한 개념
```

<br>

### Async

JavaScript는 어떤 명령이 다 끝날때 까지 기다리게 끔 프로그래밍 되어 있지않다. 

=> JavaScript는 한번에 여러가지일을 handling할 수 있게끔 만들어져 있다.

```javascript
export const home = (req, res) => {
  res.render("home", { pageTitle: "Home", videoList });
};
```

위 코드에서 비디오를 찾으면서 동시에 home 파일을 찾아서 rendering한다. 따라서 여기서 자바스크립트가 video를 다 찾은 다음에 화면을 렌더링하게끔 코드를 변경해야 하는데, 이 때 사용하는 것이 async 키워드이다.

```javascript
export const home = async (req, res) => {
    const videoList = await Video.find({}); // 이렇게 하면 Database에 있는 모든 비디오를 가지고 온다.
    res.render("home", { pageTitle: "Home", videoList });
};
//자바스크립트에세 이건 다 기다리고 다음 작업을 수행해야돼! 라고 알리는 것과 같다.await은 다음 과정이 끝날때 까지 잠시 기다려달라는 의미.(await 키워드는 반드시 async 함수 안에서만 사용할 수 있다.) 
```

성공적으로 끝나는 것을 의미하는 것이 아니라, 끝나면(에러가 발생해도 그 작업은 끝난것) 다음 작업을 실행하는 것. 따라서 발생하는 에러를 잡고 싶으면 위와 같이 코드를 짜서는 안된다.

```javascript
export const home = async (req, res) => {
    try {
        const videoList = await Video.find({});
        res.render("home", { pageTitle: "Home", videoList });
    } catch (error) {
        console.log(error);
        res.render("home", { pageTitle: "Home", videoList: [] });
    }
};

//try는 정상적으로 작동할 때, 만약에 실패하면 catch(error가 throw되면 이를 catch하겠다!)안을 실행하게끔 해서 error을 handling한다. 이렇게 코드를 짜면 에러가 발생해도 home 화면을 rendering 해서 유저에게 보여줄 수 있다.(nodeJS가 작동을 멈추지 않는다.)
```

### 파일 업로드

 비디오가 아닌 파일이 들어오지 않게 작업한다.

```pseudocode
extends layouts/main

block content
    .form-container
        form(action=`/videos${routes.upload}`, method="post", enctype="multipart/form-data")
            label(for="file") Video File
            input(type="file", id="file", name="videoFile", required=true, accept="video/*")
            input(type="text", placeholder="Title", name="title", required=true)
            textarea(placeholder="Description", name="description", required=true)
            input(type="submit", value="Upload Video")
```

accept 속성을 활용하면 특정 형태의 파일만을 받게끔 제한할 수 있다.

파일을 업로드하고 그 파일 자체를 주는 것이 아닌, 파일의 경로를 데이터에 저장해야 한다. (파일 자체를 저장하면 데이터베이스가 너무 무거워지기 때문이다.) 따라서 파일을 업로드하고 파일 경로(URL)를 반환하는 MiddleWare가 필요하다. 이 MiddleWare를 multer라고 한다. 

우선 위 코드 처럼 전체 form에 `enctype = "multipart/form-data"`를 추가해야한다. (파일을 내보내는 것이기 때문에 form의 encoding 형식이 달라야 한다.)

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install multer
```

multer를 설치하고 middlewares.js 파일에서 multer를 import해 코드를 작성한다.

```javascript
import multer from "multer";
import routes from "./routes";

const multerVideo = multer({ dest: "videoList/" });

export const localsMiddleWare = (req, res, next) => {
  res.locals.siteName = "WeTube";
  res.locals.routes = routes;
  res.locals.user = {
    isAuthenticated: true,
    id: 1
  };
  next();
};

export const uploadVideo = multerVideo.single("videoFile");


// single은 오직 하나의 파일만 업로드 할 수 있다는 것을 의미힌다. single()안에는 html에서 넘어온 input중에서 원하는 input의 name 속성 값을 담으면 된다.
```

코드 작성 뒤, videoRouter.js 파일로 가서 다음 코드를 추가한다.

```javascript
import { uploadVideo } from "../middlewares";
videoRouter.post(routes.upload, uploadVideo, postUpload);
```

마지막으로 videoController.js 파일에서 postUpload 부분을 다음과 같이 고친다.

```javascript
export const postUpload = async (req, res) => {
    const {
        body: { title, description },
        file: { path } // file을 찍어보면 file.path에 위치 값이 찍혀서 나온다.
    } = req;
    const newVideo = await Video.create({
        fileUrl: path,
        title,
        description
    });
    res.redirect(routes.videoDetail(newVideo.id));
};
```

오류 핸들링: app.js에서 다음과 같은 코드를 추가

```javascript
app.use("/uploads", express.static());// directory에서 파일을 보내주는 미들웨어, 하지만 이렇게 user에 해당하는 파일을 내 server에 저장하는 것은 좋은 방법이 아니다. 왜냐하면 수천명이 웹사이트를 사용한다고 할 때, 이 사용자들의 파일을 모두 server에 저장할 경우 파일이 의도치 않게 삭제되면 어떻게 할 것인가? 따라서 user가 생성한 파일들은 server와 분리되어야한다.
```

<br>

### Video ID 받아와 Video Detail에 반영하기 (Edit Video까지)

우선 videoController.js에서 videoDetail에 해당하는 함수를 수정해 video에 해당하는 id를 받아온다.

controller에 어떤 data를 가지고 있다는 것을 표현하고 싶으면 url에 더블콜론(:)과 이름을 넣으면 된다. (이것이 Url로부터 정보를 가져오는 유일한 방법이다.) 

videoDetail 수정

```javascript
export const videoDetail = async (req, res) => {
    const {
        params: { id }
    } = req;

    try {
        const video = await Video.findById(id);
        console.log(video);
        res.render("videoDetail", { pageTitle: "Video Detail", video });
    } catch (error) {
        console.log(error);
        res.redirect(routes.home);
    }
};
```

videoDetail.pug 수정하기

```html
extends layouts/main

block content
    .video__player
        video(src=`/${video.fileUrl}`)
    .video__info
        a(href=routes.editVideo)
        h5.video__title=video.title
        span.video__views=video.views
        p.video__description=video.description
<!-- video를 만든사람에게는 edit video를 보이게끔 해야됨. 따라서 코드를 더 작성해야한다. -->
```

editVideo.pug 수정하기

```html
extends layouts/main.pug

block content
    .form-container
        form(action=routes.editVideo(video.id), method="post")
            input(type="text", placeholder="Title", name="title", value=video.title)
            textarea(name="description", placeholder="Description")=video.description
            input(type="submit", value="Update Video")
        a.form-container__link.form-container__link--delete(href=`/videos${routes.deleteVideo}`) Delete Video
```

routes.js 파일 수정

```javascript
ideoDetail: id => {
    if (id) {
        return `/videos/${id}`;
    } else {
        return VIDEO_DETAIL;
    }
},
editVideo: id => {
     if (id) {
        return `/videos/${id}/edit`;
     } else {
        return EDIT_VIDEO;
     }
}
```

videoRouter.js에서 editVideo를 getEditVideo와 postEditVideo로 나누기

```javascript
videoRouter.get(routes.editVideo(), getEditVideo);
videoRouter.post(routes.editVideo(), postEditVideo);
```

videoController.js에서 getEditVideo 컨트롤러와 postEditVideo 컨트롤러를 생성

```javascript
export const getEditVideo = async (req, res) => {
    const {
        params: { id }
    } = req;

    try {
        const video = await Video.findById(id);
        res.render("editVideo", { pageTitle: `Edit ${video.title}`, video });
    } catch (error) {
        res.redirect(routes.home);
    }
};

export const postEditVideo = async (req, res) => {
    const {
        params: { id },
        body: { title, description }
    } = req;
    try {
        await Video.findOneAndUpdate({ id }, { title, description });
        res.redirect(routes.videoDetail(id));
    } catch (error) {
        res.redirect(routes.home);
    }
};
```

### Delete Video

delete는 post가 필요없다. 해당 url로 들어간 후 DB에서 비디오를 삭제하기만 하면 되기 때문이다.

routes.js에서 deleteVideo 부분 수정하기

```javascript
deleteVideo: id => {
    if (id) {
        return `/videos/${id}/delete`;
    } else {
        return DELETE_VIDEO;
    }
}
```

videoRouter에서 deleteVideo 함수형태로 바꾸기

```javascript
videoRouter.get(routes.deleteVideo(), deleteVideo);
```

editVideo에서 a 태그의 href 속성 바꾸기

```html
a.form-container__link.form-container__link--delete(href=routes.deleteVideo(video.id)) Delete Video
```

videoController.js에서 deleteVideo Controller 부분 아래와 같이 수정하기

```javascript
export const deleteVideo = async (req, res) => {
    const {
        params: { id }
    } = req;
    try {
        await Video.findOneAndRemove({ _id: id });
    } catch (error) {
        console.log(error);
    }
    res.redirect(routes.home);
};
```

### Video 정렬 및 검색

현재 Home 화면에서 가장 최근에 올린 영상이 가장 밑에 보이게끔 설정되어 있다. 가장 최근에 올린 영상이 가장 위에 보이게끔 재정렬 시켜보자.

videoController 코드 수정

```javascript
export const home = async (req, res) => {
    try {
        const videoList = await Video.find({}).sort({ _id: -1 });
        res.render("home", { pageTitle: "Home", videoList });
    } catch (error) {
        console.log(error);
        res.render("home", { pageTitle: "Home", videoList: [] });
    }
};
// sort method 공부할 것.
```

**정규표현식이란?**

regular expression은 string으로부터 특정 문자열을 가져오는 것을 뜻한다.(정규 표현식은 languate/ES6/Regular Expression.md 파일에 정리되어 있으므로 확인해 볼것.)

영상 검색을 할 수 있도록 regular expression을 활용해 search controller를 작성

videoController.js 파일 수정

```javascript
export const search = async (req, res) => {
    const {
        query: { term: searchingBy }
    } = req;
    let videoList = [];

    try {
        videoList = await Video.find({
            title: { $regex: searchingBy, $options: "i" }
        });
    } catch (error) {
        console.log(error);
    }
    res.render("search", { pageTitle: "Search", searchingBy, videoList });
};
```

그리고 search.pug와 videoDetail.pug도 수정.

```jade
extends layouts/main
include mixins/videoBlock

block content
    .search__header 
        h3 Searching for #{searchingBy}
    .search__videos
        if videoList.length === 0
            h5 No Videos Found
        each item in videoList
            +videoBlock({
                videoFile: item.videoFile,
                title: item.title,
                views: item.views,
                id: item.id
            })
```

```jade
extends layouts/main

block content
    .video__player
        video(src=`/${video.fileUrl}`)
    .video__info
        a(href=routes.editVideo(video.id)) Edit Video
        h5.video__title=video.title
        span.video__views=video.views
        p.video__description=video.description
    .video__comments
        if video.comments.length == 1
            span.video__comment-number 1 comment
        else
            span.video__comment-numer #{video.comments.length} comments
```

### ESLint 설치

Linter는 에러가 발생할 시, 이를 알려주는 도구이다.

eslint 설치

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install eslint -g
PS C:\Users\user\Desktop\Project\wetube> eslint --init
```

-g는 해당 package를 global하게 설치한다는 의미이다. (프로젝트 특정 폴더가 아닌, 컴퓨터 전체에서 사용할 수 있게끔 설치한다는 말.)

=> 이렇게 하니까 에러가 난다. 따라서 eslint를 제거하고 그 다음, extension에서 eslint를 설치하거나, local하게 eslint를 설치할 것.

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

