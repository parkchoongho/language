# 1. CSS 구성요소

**CSS**는 크게 2가지로 구성되어 있다.

### (1) Property

```css
property-name: value;/* 이름에 있어 중간 공백을 허용하지 않고 value 다음에 마지막으로 세미콜론(;)으로 마무리한다. */
```



### (2) Selector

위에 있는 **property**를 내 **h1** 태그에 연결시키고 싶다면?

```css
h1{
    property-name: value;
    property-name: value;
    property-name: value;
    property-name: value;
    property-name: value;
    /*property를 원하는 만큼 selector에 적용할 수 있다.*/
}
```

이렇게 작성하면 된다.

또 **selector**로 **ID** 또는 **Class**를 사용할 수 있는데 이 때는 그냥 태그와 표기법이 조금 달라진다.

```css
#id{
	property-name: value;
    property-name: value;
}

.class{
    property-name: value;
    property-name: value;
}
```



최종적으로 css는 이렇게 작성할 수 있다고 보면된다.

```css
selector (id, class, tag name){
    property-name: value;
    property-name: value;
    property-name: value;
}
```

