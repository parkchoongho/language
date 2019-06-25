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

```html
.social-login
    button
        span
            i.fab.fa-github
        |Continue with Github
```

그냥 Continue with Github로 치면 Continue를 Tag로 인식한다. 그래서 앞에 |를 붙여 Continue with Github를 Text로 인식하게끔 만들어준다.

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

### 전역적으로(글로벌) 사용할 변수 추가방법

```javascript
import routes from "./routes";

export const localsMiddleWare = (req, res, next) => {
    res.locals.siteName = "WeTube";
    res.locals.routes = routes;
    next();
};
```

<br>

### 템플릿마다 할당되는 변수를 다르게 설정하는 방법

```javascript
export const home = (req, res) => res.render("home");
// view-engine을 pug로 설정해놓았기 때문에 render함수가 자동으로 views 폴더에서 home.pug을 찾는다.
```

render 함수의 첫 번째 인자는 템플릿이고 두 번째 인자는 추가할 정보가 담긴 객체이다.

```javascript
export const home = (req, res) => res.render("home", { pageTitle: "Home" });
```

이렇게 전달할 수 있다. 전달하고 싶은 것은 무엇이든 전달할 수 있다.

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