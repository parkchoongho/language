# 1. What is HTML?

### HTML - 프로그래밍 언어가 아니다. (Hyper-Text-Mark_up-Language)

Mark_up  =>  **책을 읽으면서 중요한 부분에 밑줄을 긋는 개념!**

**마킹을 함으로써 각각의 요소가 어떤 것인지를 알려주는 언어  =>  HTML** 

**웹사이트의 요소들**을 **하이라이트**하고 밑줄 그어서 설명해주는 언어!



### index.html

보통 프로젝트에 있어 첫 html파일을 index로 명명하는데 그 이유는 웹서버들이 index 파일을 먼저 찾도록 설계되어 있기 때문이다.



### 태그의 구성요소

<이름 속성="값">내용</이름> 이렇게 대부분 구성되어 있다. (예외인 태그 존재!)

```html
<human gender="male">Human</human><!-- 실제 이런 태그는 존재하지 않는다. 이해를 돕기위한 예시 일뿐-->
```





# 2. HTML 구성

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





# 3. Tag의 종류

### (1) Semantic 태그

의미가 있는 태그 (**h1**태그는 딱 보면 헤더라는 것을 알 수 있다.)

**section, header, footer, nav, etc**



### (2) Non-Semantic 태그

아무 의미가 없는 태그(**div**와 같이 특정한 것을 지칭하지도 않는 태그 + **span** 태그)

박스 같은 것이 필요할 떄 **div**태그를 사용한다. 텍스트를 위한 컨테이너가 필요할시에는 **span** 태그





# 4. 태그에 이름짓기

```html
<html>
    <head>
    </head>
    <body>
        <section>
        	<header>
            	<h1>Title of a section</h1>
            </header>
        </section>
        <div>
            <header>Title of the unknown container</header>
        </div>
    </body>
</html>
```

이렇게 되어 있을 경우 위 **header** 태그와 아래 **header** 태그를 구별할 방법이 마땅치 않다. 여기서 명칭을 태그에 지어주는 것이 중요한데 css를 적용할 때, "이건 파란색, 이건 빨간색으로 " 같은 명령을 내려야하기 때문이다. 명칭을 하는 방법으로는 2가지가 존재한다.

### (1) Class

```html
<html>
    <head>
    </head>
    <body>
        <section>
        	<header class="headerNumberOne">
            	<h1>Title of a section</h1>
            </header>
        </section>
        <div>
            <header>Title of the unknown container</header>
        </div>
    </body>
</html>
```

**Class**는 이름이라 생각하면 편하다. 세상에 박충호라는 이름이 많듯이 **Class**는 여러번 쓰일 수 있다.



### (2) ID

```html
<html>
    <head>
    </head>
    <body>
        <section>
        	<header id="headerNumberOne">
            	<h1>Title of a section</h1>
            </header>
        </section>
        <div>
            <header>Title of the unknown container</header>
        </div>
    </body>
</html>
```

각 요소는 오직 하나의 **ID**만 가질 수 있다. 그리고 그 **ID**는 2번 쓰일 수 없다. (여권번호나 주민등록번호와 같이 생각하면 된다. **ID**는 고유하다.)

종합적으로 보면 밑에 코드와 같이 **Class**와 **ID**를 쓸 수 있다.

```html
<html>
    <head>
    </head>
    <body>
        <section>
        	<header id="headerNumberOne" class="defaultClass">
            	<h1>Title of a section</h1>
            </header>
        </section>
        <div>
            <header id="headerNumberTwo" class="defaultClass">
                Title of the unknown container
            </header>
        </div>
    </body>
</html>
```

이와 같이, **ID**는 각 요소가 유일하게 쓸 수 있고 **Class**는 같은 속성을 공유할 수 있다. 