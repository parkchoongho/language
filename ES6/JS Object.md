# JavaScript Object

### Build JavaScript Objects

`object`는 `arrays`와 비슷하지만 다른점을 가지고 있습니다. `arrays`는 index를 사용해 data에 접근하고 수정하는 반면에 `object`는 `properties`를 통해 이러한 작업을 합니다. Objects는 데이터를 구조적으로 저장하고 실세계 객체들을 표현하는데 굉장히 유용합니다.

```javascript
var cat = {
    "name": "Whiskers",
    "legs": 4,
    "tails": 1,
    "enemies": ["Water", "Dogs"]
};
```

위 코드에서 모든 properties값들은 `"name"`, `"legs"`, `"tails"` 와 같은 문자열로 구성되어 있습니다. 이러한 properties들은 문자열 뿐만아니라 숫자도 가능합니다.

```javascript
var anotherObject = {
    make: "Ford",
    5: "five",
    "model": "focus"
};
```

Tip: 이렇게 object를 설정한다고 하더라도 javascript 는 자동으로 non-string property를 string으로 type 변환시킵니다.

<br>

### Accessing Object Properties with Dot, Bracket Notation

object의 properties에 접근할 수 있는 방법은 2가지가 있습니다. 하나는 dot notation(`.`) 방법입니다. 

```javascript
var myObj = {
    prop1: "val1",
    prop2: "val2"
};
var prop1val = myObj.prop1; // val1
var prop2val = myObj.prop2; // val2
```

다른 하나는 bracket notation(`[]`)입니다. 만약 property에 중간에 space가 있는 값을 설정해 놓았다면 데이터에 접근하기 위해 이 방법을 사용해야합니다.

```javascript
var myObj = {
    "Space Name": "Kirk",
    "More Space": "Spock",
    "NoSpace": "USS Enterprise"
};
myObj["Space Name"]; // Kirk
myObj['More Space']; // Spock
myObj["NoSpace"]; // USS Enterprise
```

<br>

### Accessing Object Properties with Variables

bracket notation을 사용하는 또 다른 방법은 변수의 값을 통해서 property에 접근하는 방법입니다.

```javascript
var dogs = {
    Fido: "Mutt", Hunter: "Doberman", Snoopie: "Beagle"
};
var myDog = "Hunter";
var myBreed = dogs[myDog];
console.log(myBreed); // "Doberman"
```

```javascript
var someObj = {
    propName: "John"
};
function propPrefix(str) {
    var s = "prop";
    return s + str;
}
var someProp = propPrefix("Name"); // someProp now holds the value 'propName'
console.log(someObj[someProp]); // "John"
```

Tip: 변수를 bracket notation에 사용할 때는 변수에 quotes를 사용하지 않음에 주의하는게 좋습니다. 왜냐하면 그 변수의 값을 통해 접근하는 것이지, 변수 이름 자체를 사용하는것이 아니기 때문입니다.