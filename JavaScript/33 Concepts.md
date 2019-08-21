## 1. Call Stack

Call Stack은 자바스크립트가 함수 실행을 핸들링하는 방법 중 하나이다. 자바스크립트는 실행할 함수들을 스택(stack)위에 올린다. 스택은 일종에 쌓아올라가는 것을 생각하면 된다.(책을 쌓는다거나, 카드 스택을 만드는 등등)

함수를 실행할 때마다 위에서부터 실행하고 하나씩 스택을 제거해나간다.

```javascript
function three(){
    console.log('I love JS')
}

function two(){
    three();
}

function one(){
    two();
}

function zero(){
	one();
}

zero();
```

Call Stack 쌓이는 순서: zero => one => two => three

Call Stack 사라지는 순서: three => two => one => zero

```javascript
function three(){
    console.log('I love JS')
}

function two(){
    three();
}

function one(){
    two();
}

function zero(){
	one();
    throw Error("omg i am an error")
}

zero();
```

one 함수가 call stack에서 사라지고 난 다음(one 함수가 실행되고 종료된 후, 에러가 발생한다.)

**Tip:** 에러 메세지를 보면 에러전에 있었던 모든 콜스택을 알려준다.

