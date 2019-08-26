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

<br>

### Use Destructuring Assignment with the Rest Operator to Reassign Array Elements

array destructing을 할 때, 나머지 요소들을 하나의 array로 모으고 싶을 때 `destructing`과 `rest operator`를 같이 사용할 수 있습니다.

```javascript
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b); // 1, 2
console.log(arr); // [3, 4, 5, 7]
```

```javascript
const source = [1,2,3,4,5,6,7,8,9,10];
function removeFirstTwo(list) {
  "use strict";
  const [a,b,...arr] = list; // change this

  return arr;
}
const arr = removeFirstTwo(source);
console.log(arr); // should be [3,4,5,6,7,8,9,10]
console.log(source); // should be [1,2,3,4,5,6,7,8,9,10];
```

<br>

### Use Destructuring Assignment to Pass an Object as a Function's Parameters

object를 function argument로 destructure하는 경우가 있습니다.

```javascript
const profileUpdate = (profileData) => {
    const { name, age, nationality, location } = profileData;
    // do something with these variables
}
```

위 코드를 더 간단히 아래와 같은 코드로 바꿀 수 있습니다.

```javascript
const profileUpdate = ({ name, age, nationality, location }) => {
    /* do something with these fields */
}
```

아래 코드는 더 간결하다는 장점 외에도, 객체 전체를 조작하지 않는다는 장점을 가집니다. (오직 필요한 부분만 복사되어 함수에 전달됩니다.)

```javascript
const stats = {
  max: 56.78,
  standard_deviation: 4.34,
  median: 34.54,
  mode: 23.87,
  min: -0.75,
  average: 35.85
};
const half = (function() {
  "use strict";
  return function half({max, min}) {
  // use function argument destructuring
  return (max + min) / 2.0;
  };
 

})();
console.log(stats); // should be object
console.log(half(stats)); // should be 28.015
```

<br>

### Create Strings using Template Literals

ES6의 또 다른 특징은 *template literal*입니다. 새로운 종류의 문자열로 복잡한 문자열을 다룰 때 유용하게 활용됩니다. 

```javascript
const person = {
    name: "Zodiac Hasbro",
    age: 56
};

// Template literal with multi-line and string interpolation
const greeting = `Hello, my name is ${person.name}!
I am ${person.age} years old.`;

console.log(greeting); // prints
// Hello, my name is Zodiac Hasbro!
// I am 56 years old.
```

`template literal`은 문자열을 감싸는데 backticks(\`) 을 사용합니다. 그리고 input과 output 모두 멀티라인이므로 \n문자를 입력하지 않아도 됩니다. 그리고 `${variable}` syntax는 placeholder입니다. 이제 변수를 문자열에 사용하고 싶으면 `${}` 안에 그 변수를 입력하면 됩니다. 

<br>

### Write Concise Object Literal Declarations Using Simple Fields

ES6는 object를 정의하는데 유용한 몇가지를 제공합니다.

```javascript
const getMousePosition = (x, y) => ({
    x: x,
    y: y
});
```

`getMousePosition` 은 2개의  field를 가지고 있는 객체를 리턴하는 간단한 함수입니다. 

ES6는 `x: x` 라 써야되는 중복을 줄이고 `x` 하나만 쓰는 것을 가능케합니다. 위 코드는 따라서 아래와 같이 작성이 가능합니다.

```javascript
const getMousePosition = (x, y) => ({ x, y });
```

<br>

### Write Concise Declarative Functions with ES6

ES5에서 객체안에 함수를 정의할 때는 반드시 `function` 라는 키워드를 사용해야 했습니다.

```javascript
const person = {
    name: "Taylor",
    sayHello: function() {
        return `Hello! My name is ${this.name}.`;
    }
};
```

ES6에서는 `function` 키워드와 `:` 을 제거하고 객체안에 함수를 정의할 수 있습니다.

```javascript
const person = {
    name: "Taylor",
    sayHello() {
        return `Hello! My name is ${this.name}.`;
    }
};
```

<br>

### Use class Syntax to Define a Constructor Function

ES6는 객체를 생성할 때, keyword *class* 를 사용하여 만드는 새로운 문법을 제공합니다. 여기서 `class` syntax는 단지 syntax일뿐이며, Java나 Python에서 제공하는 객체기반 full-fledged class와는 거리가 있습니다. 

ES5에서는 생성자 함수를 정의 하고 `new` 키워드를 사용해 객체를 인스턴스화 했습니다.

```javascript
var SpaceShuttle = function(targetPlanet){
    this.targetPlanet = targetPlanet;
}
var zeus = new SpaceShuttle('Jupiter');
```

class syntax는 생성자 함수를 대체합니다.

```javascript
class SpaceShuttle {
    constructor(targetPlanet){
        this.targetPlanet = targetPlanet;
    }
}
const zeus = new SpaceShuttle('Jupiter');
```

`class` 키워드는 새로운 함수를 선언하고 생성자를 더합니다. 생성자는 `new` 키워드를 사용해 객체를 생성할 때 불려집니다.

<br>

### Use getters and setters to Control Access to an Object

객체로 부터 값들을 받아올 수 있으며 동시에 객체 property에 값을 설정할 수도 있습니다.

이를 `getters`와 `setters`라 합니다. 

Getter 함수는 유저가 private variables에 바로 접근하는 것 없이 객체의 private variables 값을 유저에게 return하는 것을 의미합니다.

Setter 함수는 setter 함수안에 값을 넣음으로써 객체의 private variable의 값을 설정하는 것을 의미합니다. 이런 설정은 계산이나, 전에 있던 값을 overwrite하는 것을 포함합니다.

```javascript
class Book {
    constructor(author) {
        this._author = author;
    }
    // getter
    get writer(){
        return this._author;
    }
    // setter
    set writer(updatedAuthor){
        this._author = updatedAuthor;
    }
}
const lol = new Book('anonymous');
console.log(lol.writer);  // anonymous
lol.writer = 'wut';
console.log(lol.writer);  // wut
```

여기서 getter, setter를 호출하기 위해 사용하는 syntax는 함수가 아닌것 처럼 보입니다. **Getters와 setters는 내부 실행의 세부사항을 숨기기 때문에 매우 중요합니다.**

```javascript
function makeClass() {
    "use strict";
    class Thermostat {
        constructor(Fahrenheit){
            this.Fahrenheit =Fahrenheit;
        }
        get temperature(){
            return 5/9*(this.Fahrenheit-32)
        }
        set temperature(Cel){
            this.Fahrenheit = Cel*9.0/5+32;
        }
    }
    return Thermostat;
}
const Thermostat = makeClass();
const thermos = new Thermostat(76); // setting in Fahrenheit scale
let temp = thermos.temperature; // 24.44 in C
thermos.temperature = 26;
temp = thermos.temperature; // 26 in C
```

**Tip**: When you implement this, you would be tracking the temperature inside the class in one scale - either Fahrenheit or Celsius.

This is the power of getter or setter - you are creating an API for another user, who would get the correct result, no matter which one you track.

In other words, you are abstracting implementation details from the consumer.

<br>

### Understand the Differences Between import and require

외부 파일이나 모듈에서 코드나 함수를 가져오기 위해 `require()` 함수를 사용했습니다. 편리하지만 이 방법은 문제점을 가지고 있었습니다: 몇몇 파일들이나 모듈들은 너무 방대해서, 거기서 특정 코드만을 따오는 것이 필요했습니다.

ES6는 `import`라는 편리한 툴을 제공합니다. 이를 사용해, 모듈이나 파일에서 우리가 원하는 특정 부분을 가져와 주어진 파일에서 활용할 수 있습니다.

아래 코드에서 `math_array_functions` 파일에서 20개의 함수를 제공한다고 가정해봅시다. 그 중, 우리가 필요한 것은 `countItems` 함수 하나 뿐입니다. `require()` 함수는 20개의 모든 함수를 가져올 수 밖에 없지만, `import` syntax를 활용하면 우리가 원하는 함수만을 가져올 수 있습니다.

```javascript
import { countItems } from "math_array_functions"
```

위 코드를 묘사하면

```javascript
import { function } from "file_path_goes_here"
// We can also import variables the same way!
```

`import` 문을 쓰는 여러 방법이 존재하는데, 위 방법이 가장 흔히 사용되는 방법입니다.

**Tip**: function을 curly braces안에 공백을 넣어 작성하는 것이 좋은 방법입니다. => `import`문을 더 쉽게 읽게하는데 도움을 줍니다. 

The lessons in this section handle non-browser features. `import`, and the statements we introduce in the rest of these lessons, won't work on a browser directly. However, we can use various tools to create code out of this to make it work in browser.

In most cases, the file path requires a `./`before it; otherwise, node will look in the `node_modules`directory first trying to load it as a dependency.

<br>

### Use export to Reuse a Code Block

위 exercise에서 처럼, `import`를 사용하기 위해서는 `export` 되어야 합니다. 다른 파일에서 재 사용할 수 있는 코드 - 함수나 변수 같은 - 를 `import`하려면, 반드시 먼저 `export` 해야 합니다. `import` 처럼 `export`는 non-browser feature입니다. 

**Tip:** non-browser feature란, 브라우저 환경 설정이외의 설정이 필요한 feature을 의미합니다. (왜냐하면 모든 브라우저가 ES6를 지원하는 것은 아니기 때문입니다. 따라서 babel과 같이 최신의 ES6 코드를 모든 브라우저가 이해할 수 있는 예전의 코드로 바꿔주는 툴이 필요합니다.)

밑에 코드는 *named export*를 보여줍니다. 이것을 활용하면, `import`를 통해 다른 파일에서 `export`한 어떤 코드든 가져올 수 있습니다.

```javascript
const capitalizeString = (string) => {
    return string.charAt(0).toUpperCase() + string.slice(1);
}
export { capitalizeString } //How to export functions.
export const foo = "bar"; //How to export variables.
```

위 코드에 있는 export 코드를 다음과 같이 한줄로 표현할 수도 있습니다.

```javascript
const capitalizeString = (string) => {
    return string.charAt(0).toUpperCase() + string.slice(1);
}
const foo = "bar";
export { capitalizeString, foo }
```

<br>

###  Use * to Import Everything from a File

현재 작업하는 파일에 모든 contents를 import 하고 싶은 파일이 있다고 합시다. 이 작업은 `import*` syntax를 통해 할 수 있습니다.

```javascript
import * as myMathModule from "math_functions";
myMathModule.add(2,3);
myMathModule.subtract(5,3);
```

```javascript
import * as object_with_name_of_your_choice from "file_path_goes_here"
object_with_name_of_your_choice.imported_function
```

You may use any name following the `import * as `portion of the statement. In order to utilize this method, it requires an object that receives the imported values. From here, you will use the dot notation to call your imported values.

<br>

### Create an Export Fallback with export default

`export default` syntax는 오직 한가지 값만 파일에서 export 될때 사용합니다. 또한 fallback value을 만들기 위해서도 사용합니다.

```javascript
export default function add(x,y) {
    return x + y;
}
```

**Tip**: Since `export default`is used to declare a fallback value for a module or file, you can only have one value be a default export in each module or file. Additionally, you cannot use `export default`with `var`, `let`, or `const`.

<br>

### Import a Default Export

`export default`를 `import`할 때는 조금 다른 `import` syntax를 사용해야합니다. 아래 `코드는 "math_functions"` 파일에서 default export된 `add` 함수를 `import` 하는 방식을 보여줍니다. 

```javascript
import add from "math_functions";
add(5,4); //Will return 9
```

보시다시피 `add`는 curly braces `{}`로 둘러 쌓이지 않습니다. Unlike exported values, the primary method of importing a default export is to simply write the value's name after `import`.

