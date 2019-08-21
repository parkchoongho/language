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

<br>

### Reusable Components with JSX + Props

JSX는 component에 정보를 실어서 보낼 수 있다. Component는 재사용이 가능하며, 반복해서 사용할 수 있다. 

App.js

```jsx
import React from "react";

function Movie() {
  return <h1>I Like Movie</h1>;
}

function App() {
  return (
    <div>
      <h1>Hello</h1>
      <Movie />
      <Movie />
      <Movie />
      <Movie />
      <Movie />
      <Movie />
      <Movie />
    </div>
  );
}

export default App;
```

만약 여러 영화리스트를 보여주고 싶으면, 위 처럼 작성하지 않고도 여러개를 보여줄 수 있다.

App.js

```jsx
import React from "react";

function Movie() {
    return <h1>I Like Movie</h1>;
}

function App() {
    return (
        <div>
            <h1>Hello</h1>
            <Movie name="Titanic" />
        </div>
    );
}

export default App;
```

Movie component에 정보를 보내고 싶으면 name="Titanic"  같이 코드를 작성하면 된다. 

(자세하게 풀면, movie component에 Titanic이라는 value로 prop name을 준 것이다.)

react는 이 props를 가져올 수 있다.

```jsx
import React from "react";

function Movie() {
    return <h1>I Like Movie</h1>;
}

function App() {
    return (
        <div>
            <h1>Hello</h1>
            <Movie name="Titanic" something={true} />
        </div>
    );
}

export default App;
```

이와같이 여러 props를 줄 수도 있다. (여러 Data 형태 전달가능) 이렇게 father component에서 children component로 원하는 많은 형태의 props를 전달 가능하다. 이렇게 보내진 props를 children component는 객체 형태로 받아올 수 있다.

```jsx
import React from "react";

function Movie({ name }) {
  return <h1>I Like {name}</h1>;
}

function App() {
  return (
    <div>
      <h1>Hello</h1>
      <Movie name="Titanic" />
    </div>
  );
}

export default App;
```

ES6의 특징인 destructing을 활용하여 위와 같이 코드를 작성할 수있다. 

`function Movie({name})` 을 이렇게 작성하면 `const { name } = props;`가 자동으로 동작하고 나서 name을 사용할 수 있게된다. 

`const { name } = props;` 이 코드는 `const name = props.name` 이랑 같다.

<br>

### Dynamic Component Generation

React에 동적인 데이터를 추가해보자. 우선 API로 부터 데이터를 가져왔다고 가정하고 그 데이터를 `const movieILike = []` 이라고 설정해보자.

App.js

```jsx
import React from "react";

function Food({ name }) {
    return <h1>I Like {name}</h1>;
}

const foodILike = [
    {
        name: "Kimchi",
        image:
        "http://aeriskitchen.com/wp-content/uploads/2008/09/kimchi_bokkeumbap_02-.jpg"
    },
    {
        name: "Samgyeopsal",
        image:
        "https://3.bp.blogspot.com/-hKwIBxIVcQw/WfsewX3fhJI/AAAAAAAAALk/yHxnxFXcfx4ZKSfHS_RQNKjw3bAC03AnACLcBGAs/s400/DSC07624.jpg"
    },
    {
        name: "Bibimbap",
        image:
        "http://cdn-image.myrecipes.com/sites/default/files/styles/4_3_horizontal_-_1200x900/public/image/recipes/ck/12/03/bibimbop-ck-x.jpg?itok=RoXlp6Xb"
    },
    {
        name: "Doncasu",
        image:
        "https://s3-media3.fl.yelpcdn.com/bphoto/7F9eTTQ_yxaWIRytAu5feA/ls.jpg"
    },
    {
        name: "Kimbap",
        image:
        "http://cdn2.koreanbapsang.com/wp-content/uploads/2012/05/DSC_1238r-e1454170512295.jpg"
    }
];

function App() {
    return (
        <div>
            <h1>Hello</h1>
            <Food name="Bulgogi" />
        </div>
    );
}

export default App;
```

**Map method**

Map method는 arry의 각 item에 function을 실행하고 그 결과값을 갖는 array를 리턴한다.

```javascript
const friends = ["dal", "mark", "lynn", "japan guy"]
friends.map(current => {
    return 0
})
// 결과 [0,0,0,0]
```

**Tip:** Component안에서 JavaScript 코드를 작성하려면  { }안에다 작성하면 된다.

```jsx
import React from "react";

function Food({ name, picture }) {
    return (
        <div>
            <h2>I Like {name}</h2>
            <img src={picture} />
        </div>
    );
}

const foodILike = [
    {
        name: "Kimchi",
        image:
        "http://aeriskitchen.com/wp-content/uploads/2008/09/kimchi_bokkeumbap_02-.jpg"
    },
    {
        name: "Samgyeopsal",
        image:
        "https://3.bp.blogspot.com/-hKwIBxIVcQw/WfsewX3fhJI/AAAAAAAAALk/yHxnxFXcfx4ZKSfHS_RQNKjw3bAC03AnACLcBGAs/s400/DSC07624.jpg"
    },
    {
        name: "Bibimbap",
        image:
        "http://cdn-image.myrecipes.com/sites/default/files/styles/4_3_horizontal_-_1200x900/public/image/recipes/ck/12/03/bibimbop-ck-x.jpg?itok=RoXlp6Xb"
    },
    {
        name: "Doncasu",
        image:
        "https://s3-media3.fl.yelpcdn.com/bphoto/7F9eTTQ_yxaWIRytAu5feA/ls.jpg"
    },
    {
        name: "Kimbap",
        image:
        "http://cdn2.koreanbapsang.com/wp-content/uploads/2012/05/DSC_1238r-e1454170512295.jpg"
    }
];

function App() {
    return (
        <div>
            {foodILike.map(dish => (
                <Food name={dish.name} picture={dish.image} />
            ))}
        </div>
    );
}

export default App;
```

<br>

### .map Recap

map은 각각 item별로 function을 호출하면서 실행된다.

위에 있는 코드처럼 작성하면 아래와 같은 오류가 발생한다.

```powershell
Warning: Each child in a list should have a unique "key" prop.

Check the render method of `App`. See https://fb.me/react-warning-keys for more information.
    in Food (at App.js:44)
    in App (at src/index.js:5)
```

위의 오류는 모든 react의 element들은 유일해야 하는데 이 element들을 list 안으로 집어넣을 때, 유일성을 잃게된다. 

=> 따라서 각가에 id를 추가해본다. 그리고 이 각각의 id를 component의 key prop에 value로 전달하면 오류가 사라진다. (각각의 element가 유일성을 가지기 때문 => key값으로 구별된다) key prop은 Food로 전달되지 않는다. 이것은 기본적으로 react 내부에서 element를 구별하기 위함이다.

```jsx
import React from "react";

function Food({ name, picture }) {
    return (
        <div>
            <h2>I Like {name}</h2>
            <img src={picture} alt={name} />
        </div>
    );
}

const foodILike = [
    {
        id: 1,
        name: "Kimchi",
        image:
        "http://aeriskitchen.com/wp-content/uploads/2008/09/kimchi_bokkeumbap_02-.jpg"
    },
    {
        id: 2,
        name: "Samgyeopsal",
        image:
        "https://3.bp.blogspot.com/-hKwIBxIVcQw/WfsewX3fhJI/AAAAAAAAALk/yHxnxFXcfx4ZKSfHS_RQNKjw3bAC03AnACLcBGAs/s400/DSC07624.jpg"
    },
    {
        id: 3,
        name: "Bibimbap",
        image:
        "http://cdn-image.myrecipes.com/sites/default/files/styles/4_3_horizontal_-_1200x900/public/image/recipes/ck/12/03/bibimbop-ck-x.jpg?itok=RoXlp6Xb"
    },
    {
        id: 4,
        name: "Doncasu",
        image:
        "https://s3-media3.fl.yelpcdn.com/bphoto/7F9eTTQ_yxaWIRytAu5feA/ls.jpg"
    },
    {
        id: 5,
        name: "Kimbap",
        image:
        "http://cdn2.koreanbapsang.com/wp-content/uploads/2012/05/DSC_1238r-e1454170512295.jpg"
    }
];

function App() {
    return (
        <div>
            {foodILike.map(dish => (
                <Food key={dish.id} name={dish.name} picture={dish.image} />
            ))}
        </div>
    );
}

export default App;
```

