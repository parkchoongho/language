# ES6

### Differences Between the var and let Keywords

```javascript
var camper = 'James';
var camper = 'David';
console.log(camper);
// logs 'David'
```

위 코드처럼 `var` 로 선언을 하게되면 변수선언을 다시한번 해도 에러없이 이를 overwrite할 수 있다. 작은 프로젝트에서는 이게 문제되지 않겠지만 코드의 길이가 길어지기 시작하면 의도치 않게 변수를 overwrite할 수 있다. 이렇게 되면 의도치 않은 에러를 발생시키고 그 에러가 어떻게 발생했는지 debugging하기가 여의치 않게된다.

`let` 키워드는 이러한 var가지고 있는 문제점을 해결하기위해 나왔다. 만일 위 코드에 `var`를 `let`으로 바꾸면 error가 발생할 것이다.

```javascript
let camper = 'James';
let camper = 'David'; // throws an error
```

따라서 `let` 키워드를 사용하면 같은 이름으로의 선언을 한번만 허용한다.

tip: `"use strict"` 을 쓰면 Strict Mode가 발동되고 이렇게 하면 쉽게 할 수 있는 오류나 안전하지 않은 코드들을 하지 못하게 잡아준다.

```javascript
"use strict";
x = 3.14; // throws an error because x is not declared
```

<br>

### Compare Scopes of the var and let Keywords

`var` 키워드로 변수를 선언했다면 그 변수는 만약에 함수안에 선언되었다면 지역변수가 될것이고 그외에는 global 변수가 되게된다.

`let` 키워드도 비슷하지만 다른점이 있다. 만약 그 변수가 선언될 때 block, statement, expression안에서 선언되었다면 그 변수의 scope는 그 block, statement, expression로 설정된다.

```javascript
var numArray = [];
for (var i = 0; i < 3; i++) {
    numArray.push(i);
}
console.log(numArray);
// returns [0, 1, 2]
console.log(i);
// returns 3
```

이렇게 선언하면 `i` 변수는 global하기 때문에 `i` 변수는 계속 남아있는다. 만일 다른 loop를 만들고 거기에 다시 `i` 변수를 선언한다면 문제가 발생할 것이다. 왜냐하면 그 loop는 그전에 updated된 global한 `i` 변수를 불러올 것이기 때문이다.

<br>

### Declare a Read-Only Variable with the const Keyword

`let` 키워드만이 새로운 변수 선언법은 아닙니다. ES6, 에서는 `const` 키워드를 사용해 변수를 선언할 수 있습니다. `const` 는 모든 `let`의 특징들을 가지며 이에 더해, **read-only**라는 특징을 가집니다. 이 말은 `const`로 변수를 선언하면 재할당될 수 없다는 것을 의미합니다.

```javascript
"use strict"
const FAV_PET = "Cats";
FAV_PET = "Dogs"; // returns error
```

`const` 키워드로 변수에 이름을 줄때는 대문자로 하고 밑줄로 단어를 구분하는 것이 좋습니다.

<br>

###  Mutate an Array Declared with const

`const` 키워드는 많은 부분에서 유용하게 사용됩니다. 몇몇 개발자들은 일단 `const` 키워드로 변수를 선언하고 만일 그 변수가 변할 필요가 있다면, 그때가서 `let` 키워드로 바꾸는 방식을 사용합니다. 

그런데  const` 변수를 가지는 objects (including arrays and functions)  ` 들은 여전히 변할 수 있습니다. `const` 변수 선언은 variable idendifier의 재할당을 방지할 뿐입니다. 아래 코드를 봅시다.

```javascript
"use strict";
const s = [5, 6, 7];
s = [1, 2, 3]; // throws error, trying to assign a const
s[2] = 45; // works just as it would with an array declared with var or let
console.log(s); // returns [5, 6, 45]
```

  