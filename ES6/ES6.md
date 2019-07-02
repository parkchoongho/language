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

  <br>

### Prevent Object Mutation

위 활동에서 본 것처럼, `const` 키워드만으로는 데이터가 변하는 것을 막을 수 없습니다. 데이터 변조를 막기 위해서, 자바스크립트는 `Object.freeze` 함수를 제공합니다. 우선 object가 frozen되면, 그 안에 있는 property 데이터들을 더 이상 더하거나, 업데이트하거나, 제거할 수 없습니다.

```javascript
let obj = {
    name:"FreeCodeCamp",
    review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad"; //will be ignored. Mutation not allowed
obj.newProp = "Test"; // will be ignored. Mutation not allowed
console.log(obj); 
// { name: "FreeCodeCamp", review:"Awesome"}
```

<br>

### Use Arrow Functions to Write Concise Anonymous Functions

자바스크립트에서 종종, 함수를 다른 함수의 argument로 전달할 때, 우리는 함수들에 이름을 붙힐 필요가 없습니다. 이런 함수들은 재사용하지 않기 때문에 이름을 붙힐 필요가 없습니다. 

```javascript
const myFunc = function() {
    const myVar = "value";
    return myVar;
}
```

위 코드를 ES6에서는 더 쉬운 **arrow function syntax** 방식으로 작성할 수 있습니다.

```javascript
const myFunc = () => {
    const myVar = "value";
    return myVar;
}
```

만약 return 값만이 존재하고 function body가 없으면, arrow function syntax는 `return` 키워드와 대괄호를 생략하는 것을 가능하게 해줍니다.

```javascript
const myFunc = () => "value";
```

일반 함수 처럼 arrow function에도 1개 또는 여러 개의 argument를 줄 수 있습니다.

```javascript
// doubles input value and returns it
const doubler = (item) => item * 2;
```

<br>

### Write Higher Order Arrow Functions

arrow function은 data를 처리하는 데 있어 굉장히 유용합니다. arrow function은 다른 function을 argument로 가지는 `map()`, `filter()`, `reduce()` 와 같은 higher order function들이 데이터를 처리하는데 있어 큰 도움을 줍니다.

```javascript
FBPosts.filter(function(post) {
    return post.thumbnail !== null && post.shares > 100 && post.likes > 500;
})
```

위 코드를 아래 코드와 비교해봅시다.

```javascript
FBPosts.filter((post) => post.thumbnail !== null && post.shares > 100 && post.likes > 500)
```

아래 코드가 더 간결하고 더 적은 줄수로 같은 것을 표현한다는 것을 알 수 있습니다.

```javascript
const realNumberArray = [4, 5.6, -9.8, 3.14, 42, 6, 8.34, -2];
const squareList = (arr) => {
  "use strict";
    
  const squaredIntegers = arr.filter((num) => num > 0 && Number.isInteger(num)).map((num) => num**2);

  return squaredIntegers;
};
// test your code
const squaredIntegers = squareList(realNumberArray);
console.log(squaredIntegers);
```

<br>

###  Set Default Parameters for Your Functions

ES6는 함수를 좀 더 유연하게 사용할 수 있게끔, `default parameters` 기능을 제공합니다.

```javascript
function greeting(name = "Anonymous") {
    return "Hello " + name;
}
console.log(greeting("John")); // Hello John
console.log(greeting()); // Hello Anonymous
```

함수 호출시, 특정 argument 값을 전달하지 않았을 때에는 미리 설정해둔 default parameter 값이 들어갑니다.

<br>

### Use the Rest Operator with Function Parameters

함수를 더 유연하게 사용하기 위해, ES6는 `rest operator` 기능을 가지고 있습니다. `rest opator`를 사용하면 입력값에 따라 argument 갯수가 바뀌는 (take variable number of arguments) 함수를 생성할 수 있습니다. 이 arguments들은 array에 저장되며 함수 내부에서 접근할 수 있습니다.

```javascript
function howMany(...args) {
    return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2)); // You have passed 3 arguments
console.log(howMany("string", null, [1, 2, 3], { })); // You have passed 4 arguments.
```

**rest operator**는 `args` array를 체킹할 필요 없게 만들고 `map(), filter(), reduce()` 함수를  parameters array에 적용될 수 있게끔합니다. (이 부분은 완벽하게 이해되지 않았으니 체킹할것. freecodecamp에 영상 있음.)

```javascript
const sum = (function() {
    "use strict";
    return function sum(...args) {
        const array = args;
        return array.reduce((a, b) => a + b, 0);
    };
})();
console.log(sum(1, 2, 3)); // 6
```

<br>

### Use the Spread Operator to Evaluate Arrays In-Place

ES5에서는 array안에 있는 요소중 최대 값을 구하려면 `apply()` method를 사용해야만 했습니다.

```javascript
var arr = [6, 89, 3, 45];
var maximus = Math.max.apply(null, arr); // returns 89
```

`Math.max(arr)`는 `NaN`을 리턴하므로 `Math.max.apply(null, arr)`를 사용해야 합니다. `Math.max()`는 array가 아닌, comma-seperated arguments를 기대하기 때문입니다. 

`spread operator` 가 이러한 문법을 더 간결하고 읽기 쉽게 만들어줍니다.

```javascript
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr); // returns 89
```

`...arr`는 unpacked 된 array를 리턴합니다. 다시 말하면 array를 *spread* 합니다.

하지만, `spread opertor`는 in-place(예를들어, 함수 argument나 array literal안)에서만 작동합니다. 

```javascript
const spreaded = ...arr; // will throw a syntax erro
```

<br>

### Use Destructuring Assignment to Assign Variables from Objects

우리는 spread로 array 요소들을 효과적으로 unpack하는 것처럼, *Destructuring assignment* syntax를 사용해 objects에도 비슷한 동작을 할 수 있습니다. 

```javascript
var voxel = {x: 3.6, y: 7.4, z: 6.54 };
var x = voxel.x; // x = 3.6
var y = voxel.y; // y = 7.4
var z = voxel.z; // z = 6.54
```

위 코드를 ES6에서는 이렇게 작성할 수 있습니다.

```javascript
var voxel = {x: 3.6, y: 7.4, z: 6.54 };
const { x, y, z } = voxel; // x = 3.6, y = 7.4, z = 6.54
```

만약에 voxel.x를 변수 `a`,  `voxel.y`를 변수 `b`, `voxel.z`를 변수 c에 할당하고 싶다면, 이렇게 작성이 가능합니다.

```javascript
const { x : a, y : b, z : c } = voxel // a = 3.6, b = 7.4, c = 6.54
```

<br>

### Use Destructuring Assignment to Assign Variables from Nested Objects

*nested objects*도 variables로 destructure 할 수 있습니다.

```javascript
const a = {
    start: { x: 5, y: 6},
    end: { x: 6, y: -9 }
};
const { start : { x: startX, y: startY }} = a;
console.log(startX, startY); // 5, 6
```

 <br>

### Use Destructuring Assignment to Assign Variables from Arrays

ES6에서는 array도 destruture 할 수 있습니다.

`spread operator`와의 차이점은 `spread opertor`는 array의 모든 요소를 unpack해서 comma-seperated list화 시키기 때문에 특정 요소를 골라 변수에 할당할 수 없습니다. `Destructuring array`는 이를 가능하게 합니다.

```javascript
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b); // 1, 2
```

변수 a에는 array의 첫번째 요소 값이 할당되었고, b에는 두번째 요소 값이 할당되었습니다. 또한 comma를 사용하여 우리가 원하는 index 값에 접근할 수 있습니다.

```javascript
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c); // 1, 2, 5
```

```javascript
let a = 8, b = 6;
(() => {
  "use strict";
  // change code below this line
  [b,a] = [a,b];
  // change code above this line
})();
console.log(a); // should be 6
console.log(b); // should be 8
```















