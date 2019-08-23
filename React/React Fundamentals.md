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

<br>

### Protection with PropTypes

prop에 잘못된 값을 주면 예기치 못한 클라이언트 상 에러가 발생할 수 있다. 따라서 prop에 알맞은 값이 들어갔는지 체크하는 절차가 필요하다. 

우선 prop-types를 설치한다.

```powershell
PS C:\Users\user\Desktop\Project\movie_app_react> npm install prop-types
```

이 prop-types 모듈은 내가 전달받은 props가 원하는 props인지 확인해주는 역할을 한다.

사용방법은 import를 사용해 불러온 후, proptypes를 활용할 수 있다.

```jsx
import React from "react";
import PropTyes from "prop-types";

const foodILike = [
  {
    id: 1,
    name: "Kimchi",
    image:
      "http://aeriskitchen.com/wp-content/uploads/2008/09/kimchi_bokkeumbap_02-.jpg",
    rating: 5
  },
  {
    id: 2,
    name: "Samgyeopsal",
    image:
      "https://3.bp.blogspot.com/-hKwIBxIVcQw/WfsewX3fhJI/AAAAAAAAALk/yHxnxFXcfx4ZKSfHS_RQNKjw3bAC03AnACLcBGAs/s400/DSC07624.jpg",
    rating: 4.5
  },
  {
    id: 3,
    name: "Bibimbap",
    image:
      "http://cdn-image.myrecipes.com/sites/default/files/styles/4_3_horizontal_-_1200x900/public/image/recipes/ck/12/03/bibimbop-ck-x.jpg?itok=RoXlp6Xb",
    rating: 4.9
  },
  {
    id: 4,
    name: "Doncasu",
    image:
      "https://s3-media3.fl.yelpcdn.com/bphoto/7F9eTTQ_yxaWIRytAu5feA/ls.jpg",
    rating: 5
  },
  {
    id: 5,
    name: "Kimbap",
    image:
      "http://cdn2.koreanbapsang.com/wp-content/uploads/2012/05/DSC_1238r-e1454170512295.jpg",
    rating: 4.3
  }
];

function Food({ name, picture, rating }) {
  return (
    <div>
      <h2>I Like {name}</h2>
      <h4>{rating} / 5.0</h4>
      <img src={picture} alt={name} />
    </div>
  );
}

Food.propTyes = {
  name: PropTyes.string.isRequired,
  picture: PropTyes.string.isRequired,
  rating: PropTyes.number.isRequired
};

function App() {
  return (
    <div>
      {foodILike.map(dish => (
        <Food
          key={dish.id}
          name={dish.name}
          picture={dish.image}
          rating={dish.rating}
        />
      ))}
    </div>
  );
}

export default App;
```

만약 `PropTypes.number.isRequired` 에서 isRequired를 삭제하면 undefined도 허용한다는 의미이다. (number 또는 undefined를 허용하겠다는 뜻)

`Food.propTypes` 는 반드시 propTypes로 작성해야 react가 체크할 수 있다.

<br>

### Class Components and State

state는 보통 동적 데이터(dynamic data)로 작업할 때 사용한다. 우선 지금까지 작성한 정직인 데이터를 삭제하고 function component를 class component로 변경하자.

`class App extends React.Component`

=> App class가 React class component로부터 가져오고 있다는 뜻.

Class React Component는 return을 가지지 않는다. 왜냐하면, function이 아니기 때문이다. 그 대신에 render method를 가지고 있다. 

```jsx
class App extends React.Component{
    render(){}
}
```

React Component가 render method를 가지고 있기 때문에 extends를 통해 App class도 이제 render method가 있다.

```jsx
import React from "react";

class App extends React.Component {
  render() {
    return <h1>I am a Class Component.</h1>;
  }
}

export default App;
```

react는 자동으로 class component의 render method를 실행한다.

function component 대신 class component를 사용하는 이유는 바로 state이다. state는 객체이고 component의 data를 넣을 공간이며 이 데이터는 변한다.

```jsx
import React from "react";

class App extends React.Component {
  state = {
    count: 0
  };
  render() {
    return <h1>I am a Class Componen {this.state.count}</h1>;
  }
}

export default App;
```

class이므로 state만 써서는 안되고 `this.state`라고 써야한다. 그렇다면 변하는 데이터를 react에서는 어떻게 입력하고 활용할 수 있을까?

```jsx
import React from "react";

class App extends React.Component {
  state = {
    count: 0
  };

  add = () => {
    console.log("Add");
  };

  minus = () => {
    console.log("Minus");
  };

  render() {
    return (
      <div>
        <h1>I am a Class Component {this.state.count}</h1>
        <button onClick={this.add}>Add</button>
        <button onClick={this.minus}>Minus</button>
      </div>
    );
  }
}

export default App;
```

JavaScript에서는 "click" 이벤트를 eventListener에 등록하는 방법등을 사용하는데 react에서는 자동적으로 onClick prop을 가지고 있다.

`this.add` 라고 적는 이유는 이 JavaScript 파일이 로드되면서 바로 실행되는 것이 아닌,(this.add()는 바로 실행된다.) click 했을 때만  함수가 호출되기를 원하기 때문이다.

<br>

### All you need to know about State

위에서 이해한 State를 활용하고자 할 때, state를 직접 변경해서는 안된다. state 값을 직접 변경하면 브라우저에 반영이 되지 않는데, 왜냐하면 react가 reder function을 refresh하지 않기 때문이다.

=> 매번 state 상태가 변경될 때, react가 render function을 호출해서 바꾸길 원한다는 의미.

**따라서 setState function을 호출하면, react는 스마트해서 언제 setState를 호출할 지를 알고 또한 view를 refresh하길 원하는 것을 알고 render function을 refresh하길 원하는 것을 안다**. 

```jsx
import React from "react";

class App extends React.Component {
  state = {
    count: 0
  };

  add = () => {
    this.setState({ count: 1 });
  };

  minus = () => {
    this.setState({ count: -1 });
  };

  render() {
    return (
      <div>
        <h1>I am a Class Component {this.state.count}</h1>
        <button onClick={this.add}>Add</button>
        <button onClick={this.minus}>Minus</button>
      </div>
    );
  }
}

export default App;
```

setState는 새로운 state를  취해야한다. 

이렇게 코드를 작성을 하면 전체 page를 렌더링하지 않고 변화가 있는 부분만 react가 업데이트한다. (Virtual DOM을 가지고 있기 때문에 가능한 작업)

```jsx
import React from "react";

class App extends React.Component {
  state = {
    count: 0
  };

  add = () => {
    this.setState({ count: this.state.count + 1 });
  };

  minus = () => {
    this.setState({ count: this.state.count - 1 });
  };

  render() {
    return (
      <div>
        <h1>I am a Class Component {this.state.count}</h1>
        <button onClick={this.add}>Add</button>
        <button onClick={this.minus}>Minus</button>
      </div>
    );
  }
}

export default App;
```

이 코드 방법도 state를 직접적으로 다루므로 좋은 방법이 아니다. (성능 문제가 있다고 하는데 자세한거는 아직 모름) 그런데 react는 현재 state를 가져올 수 있는 방법을 제공한다.

(state를 설정할 때, 외부의 상태에 의존하지 않는 가장 좋은 방법이다.)

```jsx
import React from "react";

class App extends React.Component {
  state = {
    count: 0
  };

  add = () => {
    this.setState(current => ({
      count: current.count + 1
    }));
  };

  minus = () => {
    this.setState(current => ({
      count: current.count - 1
    }));
  };

  render() {
    return (
      <div>
        <h1>I am a Class Component {this.state.count}</h1>
        <button onClick={this.add}>Add</button>
        <button onClick={this.minus}>Minus</button>
      </div>
    );
  }
}

export default App;
```

**반드시 기억할것**: setState를 호출하는 매 순간, react는 새로운 state와 함께 render function을 호출한다. (다시 rendering을 한다는 뜻)

<br>

### Component Life Cycle

위 코드에서 우리가 React Component에서 사용하는 유일한 함수는 render 함수이다. React Class Component 이보다 더 많은 기능을 가지고 있다. 그 중 life cycle method가 있다.



**Life Cycle Method**

life cycle method는 기본적으로 react가 component를 생성하고 없애는 방법이다. 

Component가 생성될 때, render 전에 호출되는 몇개의 function들이 존재하며, render가 된 후, 호출되는 또 다른 function들이 존재한다. 

이 중에 필요한 함수들을 카테코리별로 소개한다.



**Mounting**

Mounting은 태어나는 것과 같다.

- constructor()

react에서 온 것이 아니며, JavaScript에서 class를 만들 때 호출되는 것이다. 

- render()

constructor()가 호출되고 그 다음 render()가 호출된다. 

- componentDidMount()

component가 render 될 때, 이 component가 처음 render 되었다고 알려준다.



**Updating**

일반적인 업데이트를 뜻한다. (위 코드에서 Add눌러 상태를 변경하는 것을 업데이트라 한다.)

- render()
- componentDidUpdate()

State를 바꾸면 component를 호출하고 먼저 render를 호출한 다음에, 업데이트가 완료되면 componentDidUpdate()가 실행된다.



**Unmounting**

Component가 죽는 것을 의미한다. (페이지를 바꿀 때, state를 사용해 component를 교체 등등)

- componentWillUnmount

component가 사라질 때, 호출된다.

참고자료: http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/

<br>

### Planning the Movie Component

위에서 배운 사항을 바탕으로 이제 Movie Component를 생성해보자.

우선 application가 작동하자마자 생겨나는 것이 바로 mount이다.

```jsx
import React from "react";

class App extends React.Component {
  state = {
    isLoading: true,
    movies: []
  };
  componentDidMount() {
    setTimeout(() => {
      this.setState({ isLoading: false });
    }, 6000);
  }
  render() {
    const { isLoading } = this.state;
    return <div>{isLoading ? "Loading..." : "We are ready"}</div>;
  }
}

export default App;
```

브라우저가 작동하기 시작하면 로딩되는 것이 맞으므로 isLoading 값을 true로 설정했다. 그래서 삼항연산자를 활용해 이를 구성한다. 그 다음, render를 하기 시작하면 componentDidMount를 호출한다.

setTimeout은 delay function이다. 6초 후에 rendering이 완료된 것처럼 설정.

이론적으로 우리가 할 일은 componentDidMount에서 data를 fetch하는 작업이다. 그리고 API로부터 data fetching을 완료하면 "We are redy" 대신 Movie Component를 render한다.

state를 미리 선언하지않고 나중에 state를 추가(state에 선언하지 않은 값을 setState에서 넣어준 경우)해도 에러가 발생하지는 않지만 미리 선언하는 것이 좋은 코딩 기법이다. (프로그래머의 버릇마다 다른데, 나는 개인적으로 미리 선언하는 것을 선호)

<br>

### Fetching Movies from API

일반적으로 사람들이 JavaScript에서 data를 fetch하는 방법은 fetch를 사용하는 것이다. 그런데 여기서는 axios를 사용해볼 예정이다.

**Axios**

axios는 fetch위에 있는 작은 layer라 생각하면 된다. (땅콩을 둘러싸고 있는 초콜릿 같은 느낌?)

axios 설치

```powershell
PS C:\Users\user\Desktop\Project\movie_app_react> npm install axios
```

`axios.get("https://yts-proxy.now.sh/list_movies.json")` 

이렇게 코드를 작성하면 axios가 json형태의 데이터를 우리에게 준다. 

```jsx
import React from "react";
import axios from "axios";

class App extends React.Component {
  state = {
    isLoading: true,
    movies: []
  };
  getMovies = async () => {
    const movies = await axios.get("https://yts-proxy.now.sh/list_movies.json");
  };

  async componentDidMount() {
    this.getMovies();
  }
  render() {
    const { isLoading } = this.state;
    return <div>{isLoading ? "Loading..." : "We are ready"}</div>;
  }
}

export default App;
```

주의해야할 점은 axios가 항상 빠르게 동작하지 않는다는 점이다. 따라서 JavaScript에게 axios의 동작이 끝날 때까지 기다려야 한다는 것을 알려야한다. 따라서 여기에 `async await` 방식을 적용한다.

=> async를 통해 이 함수가 비동기라고 알리고 함수 내부에서는 어떤 작업을 기다려야 되는지를 await를 통해 알려준다. (async없이는 await을 쓸 수 없다.)

