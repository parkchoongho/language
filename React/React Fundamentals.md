# React Fundamentals

react 프로젝트 설치

```powershell
PS C:\Users\user\Desktop\Project> npx create-react-app movie_app_react
```

### How does React work?

create-react-app에서는 자동으로 수정한 코드를 브라우저에 반영해준다.

react는 거기에 작성하는 모든 요소를 생성한다는 것이다. 자바스크립트와 함께 이를 만들고 그것들을 HTML로 밀어넣는 작업을 한다. 

index.html

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <link rel="shortcut icon" href="%PUBLIC_URL%/favicon.ico" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <meta name="theme-color" content="#000000" />
        <meta
              name="description"
              content="Web site created using create-react-app"
              />
        <link rel="apple-touch-icon" href="logo192.png" />
        <!--
manifest.json provides metadata used when your web app is installed on a
user's mobile device or desktop. See https://developers.google.com/web/fundamentals/web-app-manifest/
-->
        <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
        <!--
Notice the use of %PUBLIC_URL% in the tags above.
It will be replaced with the URL of the `public` folder during the build.
Only files inside the `public` folder can be referenced from the HTML.

Unlike "/favicon.ico" or "favicon.ico", "%PUBLIC_URL%/favicon.ico" will
work correctly both with client-side routing and a non-root public URL.
Learn how to configure a non-root public URL by running `npm run build`.
-->
        <title>React App</title>
    </head>
    <body>
        <noscript>You need to enable JavaScript to run this app.</noscript>
        <div id="root"></div>
        <!--
This HTML file is a template.
If you open it directly in the browser, you will see an empty page.

You can add webfonts, meta tags, or analytics to this file.
The build step will place the bundled scripts into the <body> tag.

To begin the development, run `npm start` or `yarn start`.
To create a production bundle, use `npm run build` or `yarn build`.
-->
    </body>
</html>
```

보이는 것 처럼 `<div id="root"></div>` 에는 아무것도 없다. 리액트는 바로 이러한 곳에 element를 넣는 역할을 한다.

index.js

```javascript
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```

App.js

```javascript
import React from "react";

function App() {
    return <div className="App">Hello</div>;
}

export default App;
```

=> id가 'root'인 DOM안에  `<App />` 를 넣겠다.

React는 소스코드에 처음부터 HTML 넣지않고 HTML을 추가하거나 제거하는 방법을 알고 있다. 따라서 application은 맨 처음에는 빈 화면을 load하고 그 다음에 react가 component에 작성해둔 것들을  HTML에 밀어넣는다. 

**Virtual DOM**

Virtual Document Object Model 

=> 말 그대로 소스코드에는 존재하지 않는 다는 말이다. (react가 그것을 만들어낸다.)

이것이 react가 빠른 이유이다. (가상이고 존재하지 않기 때문이다.)

<br>

### Creating First React Component

index.js

```javascript
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```

기본적으로 `<App />` 이것을 component라 부른다. 그리고 react는 기본적으로 component와 함께 동작하게 되어있다.

**What is Component?**

Component는 기본적으로 HTML을 반환하는 함수이다. JavaScript와 HTML 사이의 이러한 조합을 JSX라한다. (JSX는 React에 특화된 거의 유일한 개념이다. 나머지는 JavaScript 개념)

react application은 한 번에 하나의 component만 rendering 할 수 있다.

`ReactDOM.render(<App /><Potato />, document.getElementById("root"));`

위와 같은 코드 불가능