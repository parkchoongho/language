# User Authentication

### Passport

사용자 인증을 도와주는 미들웨어이다. 

**인증**이란, 브라우저 상에 쿠키(Cookies)를 설정하면 쿠키를 통해 유저의 ID를 알게되고 Passport가 인증이 완료된 User Object를 controller에 넘겨주게 된다. 사용하고 통합시키는데 유용한 미들웨어.

**쿠키**란, 쿠키는 브라우저에 저장할 수 있는 어떤 것들을 의미하는데, 요청이 발생하면 브라우저는 자동적으로 쿠키들을 서버로 전송해준다. 

=> 여기서 Passport가 하는 역할은 쿠키를 생성하고 브라우저에 저장하고 유저에게 해당 쿠키를 주는 역할.

**passport-local**은 username과 password를 사용하는 사용자 인증 방식(strategy)을 의미한다.

**serialization**이란?

=> 어떤 정보를 쿠키에 주느냐를 의미한다. (웹 브라우저에 있는 사용자에 대해, 어떤 정보를 가질 수 있는냐) 다시 말해, 어떤 field가 쿠키에 포함될 것인가를 알려준다.

**Tip**: 쿠키는 작아야 좋고, 민감한 정보는 절대 담지 말것! (다른 누군가가 쿠키에 접근할 수 있기 때문이다.) 

**serializeUser** 함수는 어떤 정보를 담을 것인가를 결정하고, **deserializeUser** 함수는 어느 사용자인지 어떻게 찾는가를 결정한다.

passport, passport-local, passport-local-mongoose 설치

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install passport-local-mongoose
```

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install passport passport-local
```

User.js 생성

```javascript
import mongoose from "mongoose";
import passportLocalMongoose from "passport-local-mongoose";

const UserSchema = new mongoose.Schema({
  name: String,
  email: String,
  avatarUrl: String,
  facebookId: Number,
  githubId: Number
});

UserSchema.plugin(passportLocalMongoose, { usernameField: "email" });

const model = mongoose.model("User", UserSchema);

export default model;
```

init.js에 User 모델 추가

```javascript
import "./models/User";
```

passport.js 생성

```javascript
import passport from "passport";
import User from "./models/User";

passport.use(User.createStrategy());

passport.serializeUser(User.serializeUser());
passport.deserializeUser(User.deserializeUser());
```

userController.js에서 postJoin 컨트롤러 함수 수정

```javascript
export const postJoin = async (req, res) => {
    const {
        body: { name, email, password, veriPassword }
    } = req;

    if (password !== veriPassword) {
        res.status(400);
        res.render("join", { pageTitle: "Join" });
    } else {
        try {
            const user = await User({
                name,
                email
            });
            await User.register(user, password);
        } catch (error) {
            console.log(error);
        }

        // Todo: Log user in
        res.redirect(routes.home);
    }
};
```

<br>

### 회원가입 후, 자동 로그인

global Router.js

```javascript
import express from "express";
import routes from "../routes";
import { home, search } from "../controllers/videoController";
import {
  logout,
  getJoin,
  postJoin,
  getLogin,
  postLogin
} from "../controllers/userController";

const globalRouter = express.Router();

globalRouter.get(routes.join, getJoin);
globalRouter.post(routes.join, postJoin, postLogin);

globalRouter.get(routes.login, getLogin);
globalRouter.post(routes.login, postLogin);

globalRouter.get(routes.home, home);
globalRouter.get(routes.search, search);
globalRouter.get(routes.logout, logout);

export default globalRouter;
```

globalRouter.post(routes.join, postJoin, postLogin)에서 postJoin에서 받은 username(여기서는 email)과 password 정보들을 postLogin으로 보내서 인증하도록 한다. 현재 passport 인증 방식은 항상 username과 passport를 찾도록 설정되어 있다.

userController.js에서 postJoin 컨트롤러와 postLogin 컨트롤러 수정

(next를 추가하고 성공하면 next를 통해 postLogin 함수를 불러와 자동으로 로그인이 되게끔 설정, postLogin은 미리 설정해 놓은 local strategy로 인증하고 실패하면 /login 성공하면 /으로 리다이렉트 하도록 설정) 

```javascript
export const postJoin = async (req, res, next) => {
  const {
    body: { name, email, password, veriPassword }
  } = req;

  if (password !== veriPassword) {
    res.status(400);
    res.render("join", { pageTitle: "Join" });
  } else {
    try {
      const user = await User({
        name,
        email
      });
      await User.register(user, password);
      next();
    } catch (error) {
      console.log(error);
      res.redirect(routes.home);
    }
  }
};

export const postLogin = passport.authenticate("local", {
  failureRedirect: routes.login,
  successRedirect: routes.home
});
```

app.js 수정

(쿠키가 설정되면 passport가 초기화 된 후, 자동으로 설정할 수 있도록 passport.initialize(), passport.session()를 추가한다. => 순서가 중요. 그 다음 요청에서 localsMiddleWare.js에서 user을 가져올 수 있도록 위치시킨다.)

```javascript
import express from "express"; // import express
import morgan from "morgan";
import helmet from "helmet";
import cookieParser from "cookie-parser";
import bodyParser from "body-parser";
import passport from "passport";
import { localsMiddleWare } from "./middlewares";
import routes from "./routes";
import globalRouter from "./routers/globalRouter";
import userRouter from "./routers/userRouter";
import videoRouter from "./routers/videoRouter";
import "./passport";

const app = express(); // call express

app.use(helmet());
app.set("view engine", "pug");
app.use("/uploads", express.static("uploads"));
app.use("/static", express.static("static"));
app.use(cookieParser());
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));
app.use(morgan("dev"));
app.use(passport.initialize());
app.use(passport.session());
app.use(localsMiddleWare);

app.use(routes.home, globalRouter); // 전역적 Router
app.use(routes.users, userRouter);
app.use(routes.videos, videoRouter);

export default app;
```

middlewares.js 수정

(모든 페이지에서 user를 가져올 수 있도록 res.locals.user = req.user || {} 를 작성. => 만일 없을 경우에는 빈 객체 {}를 준다.)

```javascript
import multer from "multer";
import routes from "./routes";

const multerVideo = multer({ dest: "uploads/videoList/" });

export const localsMiddleWare = (req, res, next) => {
  res.locals.siteName = "WeTube";
  res.locals.routes = routes;
  res.locals.user = req.user || {};
  next();
};

export const uploadVideo = multerVideo.single("videoFile");
```

<br>

### Express-Session 

Express-Session은 세션을 관리하는데 필요한 프로그램이다. Express는 궁극적으로 session을 통해 cookie를 관리할 수 있게 된다.

Express-Session 설치

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install express-session
```

session에는 secret이라 불리는 중요한 option이 있는데, 무작위 문자열로 쿠키에 들어있는 session ID를 암호화하기 위한 장치이다.(예를 들어, session ID를 전송할 때 그 값 그대로 전송하는 것이 아니다.   => 암호화하여 전송) 따라서 secret은 필수적으로 required되는 옵션이다.

randomkeygen에서 문자열을 가져와 secret에 할당한다. => 이때, secret에 바로 할당하지 말고 환경변수(.env)에 넣자 

=> 왜냐하면 다른 사람들이 secret이 어떻게 되는지 모르게 하기위해서 (누군가 알게되면 우리 쿠키를 해독하여 사용할 수 있기 때문)

.env에 설정

```
MONGO_URL="mongodb://localhost:27017/wetube"
PORT=3000
COOKIE_SECRET = "B5mC:AuCMULL[2Ce7FN3zNgU|w.<UJ"
```

app.js 수정

```javascript
import express from "express"; // import express
import morgan from "morgan";
import helmet from "helmet";
import cookieParser from "cookie-parser";
import bodyParser from "body-parser";
import passport from "passport";
import session from "express-session";
import { localsMiddleWare } from "./middlewares";
import routes from "./routes";
import globalRouter from "./routers/globalRouter";
import userRouter from "./routers/userRouter";
import videoRouter from "./routers/videoRouter";
import "./passport";

const app = express(); // call express

app.use(helmet());
app.set("view engine", "pug");
app.use("/uploads", express.static("uploads"));
app.use("/static", express.static("static"));
app.use(cookieParser());
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));
app.use(morgan("dev"));
app.use(
  session({
    secret: process.env.COOKIE_SECRET,
    resave: true,
    saveUninitialized: false
  })
);
app.use(passport.initialize());
app.use(passport.session());
app.use(localsMiddleWare);

app.use(routes.home, globalRouter); // 전역적 Router
app.use(routes.users, userRouter);
app.use(routes.videos, videoRouter);

export default app;
```

이 상태에서 로그인하고 그 다음, 서버를 재가동시키면 session이 유지되지 않는다. (서버는 어느 사용자가 어느 쿠키를 가지고 있는지를 계속해서 기억하고 있어야 한다. 이렇게 세션을 유지못하는 것은 서버가 재가동될시, 누가 누군지를 판별할 수 없게 되는 것과 마찬가지)