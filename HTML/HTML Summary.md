# 1. What is HTML?

HTML - 프로그래밍 언어가 아니다. (Hyper-Text-Mark_up-Language)

Mark_up  =>  **책을 읽으면서 중요한 부분에 밑줄을 긋는 개념!**

**마킹을 함으로써 각각의 요소가 어떤 것인지를 알려주는 언어  =>  HTML** 

**웹사이트의 요소들**을 **하이라이트**하고 밑줄 그어서 설명해주는 언어!





# 2. What tags does HTML have?

### index.html

보통 프로젝트에 있어 첫 html파일을 index로 명명하는데 그 이유는 웹서버들이 index 파일을 먼저 찾도록 설계되어 있기 때문이다.

### 태그의 구성요소

<이름 속성="값">내용</이름> 이렇게 대부분 구성되어 있다. (예외인 태그 존재!)

```html
<human gender="male">Human</human><!-- 실제 이런 태그는 존재하지 않는다. 이해를 돕기위한 예시 일뿐-->
```





# 3. HTML 구성

```html
<!DOCTYPE html> <!-- 이 태그는 이 html파일이 HTML5임을 말해준다. 또한, 이 태그는 self-contained 태그로서 스스로 열고 닫는 태그이다.(그 자체로 정보를 제공하기 때문에 이런 방식으로 작성)-->
<html>
    <head>
        <!--head부분은 유저에게 보이지 않는다. head는 브라우저에게 웹사이트에 관해 필요한 정보를 제공하는 태그이다.-->
        <meta charset="utf-8"> 
        <!--meta는 엑스트라, 추가정보와 같은 뜻이다. charset은 문자 인코딩에 대한 정보를 내포한다.-->
        <meta name="description" content="Welcome My Website!">
        <meta name="author" content="Park Choong Ho"> 
        <!--구글에서 검색하면 나오는 웹사이트를 보면 링크 밑에 그 사이트에 대한 설명이 나온다. 그걸 위해 사용하는 속성 다양한 종류의 meta태그가 존재한다. 어떤 태그는 트웨터, 네이버, 페이스북 등 특정 플랫폼만을 위해 존재하기도 함.-->
        <title>This is my title</title>
    </head>
    <body>
    </body>
</html>

<!-- 문서는 크게 2가지로 나뉜다. head 부분과 body 부분 -->
```