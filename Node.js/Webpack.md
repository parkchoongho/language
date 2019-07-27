# Webpack

Webpack은 modlue bundler로써 많은 파일들을 webpack에게 주면, webpack은 그 파일들을 호환되는 static 파일들로 변환해서 준다.

(쉽게 말해, 최신 코드들, Sass나 ES6등과 같은 코드들을 브라우저가 알아들을 수 있는 css나 js로 변환시켜주는 것이라 생각하면 된다.)

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install webpack webpack-cli
```

webpack-cli는 터미널에서 webpack을 사용할 수 있게 해주는 것이다.

설치 후, webpack.config.js 라는 파일을 생성해준다. 생성위치는 프로젝트 폴더 바로 안쪽. 

그리고 package.json 파일을 scripts 부분을 아래와 같이 변경한다.

```javascript
"scripts": {
    "dev:server": "nodemon --exec babel-node init.js --delay 2",
    "dev:assets": "webpack"
}
```

기본적으로 webpack은 expoted configuratoin object를 찾는다. config 파일 안에서 명심할 것은, server 코드와 연관시키지 않는다는 점이다. (webpack.config.js안에 들어갈 코드는 100% client code) 

webpack은 크게 2가지로 불리우는데, 하나는 entry이고, 다른 하나는 output이다. entry는 파일이 어디에서 왔는가? 이고 output은 이것을 어디에 넣을 것인가? 이다.

assets 폴더를 생성한다. 생성위치는 webpack.config.js 처럼 프로젝트 폴더 바로 안쪽. 그리고 assets 폴더안에다가 js라는 폴더와 assets라는 폴더를 만든다. 그리고 js 폴더에는 main.js scss에는 styles.scss라는 파일을 생성한다.

그리고 Node.js에서는 파일과 디렉토리 경로를 absolute하게 만들어주는 방법이 존재한다. (다시 말해, 컴퓨터나 서버에서의 전체 경로를 갖게되는 것이다.) path라는 것을 통해 가능하고 이 패키지는 Node.js에 기본으로 설치되어 있는 패키지다. __dirname 현재 프로젝트 디렉토리 이름인데, 어디서든 접근 가능한, Node.js 전역변수이다.

```javascript
const path = require("path");
const ExtractCSS = require("extract-text-webpack-plugin");

const MODE = process.env.WEBPACK_ENV;
const ENTRY_FILE = path.resolve(__dirname, "assets", "js", "main.js");
const OUTPUT_DIR = path.join(__dirname, "static");

const config = {
    entry: ENTRY_FILE,
    mode: MODE,
    module: {
        rules: [
            {
                test: /\.(scss)$/,
                use: ExtractCSS.extract([
                    {
                        loader: "css-loader"
                    },
                    {
                        loader: "postcss-library"
                    },
                    {
                        loader: "sass-loader"
                    }
                ])
            }
        ]
    },
    output: {
        path: OUTPUT_DIR,
        filename: "[name].[format]"
    }
};

module.exports = config;

```

loader란, 기본적으로 webpack에게 파일을 처리하는 방법을 알려주는 역할을 한다. webpack은 아무것도 할줄 모르기에, loader를 추가해야 비로소 파일을 handling할 수 있는 능력이 생긴다.

```powershell
PS C:\Users\user\Desktop\Project\wetube> npm install extract-text-webpack-plugin@next
```

npm에서 새로운 버전을 설치하고 싶으면, @ 기호를 쓰는 방법도 있다.

webpack은 config 파일에서, 아래에서 위로 진행된다.