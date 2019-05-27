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