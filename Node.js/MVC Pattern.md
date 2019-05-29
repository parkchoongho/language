# 	1. What is MVC Pattern?

### 	1) M Model 

=> Data

### 	2) V View

=> How does the data look

### 	3) C Control

=> Function that looks for the data, 어떤일이 발생할지에 대한 일종의 로직



#### 대개 프로젝트에 존재하는 각 Model마다 Controller를 생성한다.



#### Router

```javascript
const VIDEO_DETAIL = "/:id";
const EDIT_VIDEO = "/:id/edit";
const DELETE_VIDEO = "/:id/delete";
```

Router가 똑똑해서 이렇게 url을 설정하면 id가 변하는 값임을 알아챈다.



# 2. View

### app.set(name, value)

.set함수는 application의 설정을 하는 함수이다.

### 컨트롤러에 설정되어있는 send를 render로 바꿔준 후에 pug파일을 연결하면 된다.

```javascript
export const home = (req, res) => res.render("home");
export const search = (req, res) => res.send("Search");

export const videos = (req, res) => res.send("Videos");
export const upload = (req, res) => res.send("Upload");
export const videoDetail = (req, res) => res.send("Video Detail");
export const editVideo = (req, res) => res.send("Edit Video");
export const deleteVideo = (req, res) => res.send("Delete Video");
```

### Pug

Pug는 Express에서 View를 다루는 방식 중 하나이다. HTML이 멋지게 보이게 만들어준다. HTML과 CSS로만 작업할 경우, 반복되는 일을 너무 많이 하게돼 좋지않다. 단순작업을 하는 대신 pug를 사용하면 논리적으로 View를 관리할 수 있다.

(밑 코드는 pug코드이다.)

```html
doctype html
html
    head
        title Wetube
    body
        main
            block content
        footer
            span &copy; Wetube
```

block content 이 부분에 다른 화면들의 내용들이 들어간다.



### How to put javascript code in pug?

```pug
footer.footer
    .footer__icon
        i.fab.fa-youtube
    span.footer__text Wetube #{new Date().getFullYear()} &copy; 
```



### One Single Source of Truth

한곳에서만 정보를 보관. 코드를 더 좋게 만드는 원칙중 하나. 이 방식으로 코드를 짠다면 버그를 최소화 할 수 있다.





### 전역적으로(글로벌) 사용할 변수 추가방법

```javascript
import routes from "./routes";

export const localsMiddleWare = (req, res, next) => {
    res.locals.siteName = "WeTube";
    res.locals.routes = routes;
    next();
};
```



### 템플릿마다 할당되는 변수를 다르게 설정하는 방법

```javascript
export const home = (req, res) => res.render("home");
```

render 함수의 첫 번째 인자는 템플릿이고 두 번째 인자는 추가할 정보가 담긴 객체이다.

```javascript
export const home = (req, res) => res.render("home", { pageTitle: "Home" });
```

이렇게 전달할 수 있다. 전달하고 싶은 것은 무었이든 전달할 수 있다.