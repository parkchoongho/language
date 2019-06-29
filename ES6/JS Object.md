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

**Tip**: 이렇게 object를 설정한다고 하더라도 javascript 는 자동으로 non-string property를 string으로 type 변환시킵니다.

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

**Tip**: 변수를 bracket notation에 사용할 때는 변수에 quotes를 사용하지 않음에 주의하는게 좋습니다. 왜냐하면 그 변수의 값을 통해 접근하는 것이지, 변수 이름 자체를 사용하는것이 아니기 때문입니다.

<br>

### Updating Object Properties

object를 만든 후에는 변수값을 변경하는 것처럼 언제든지 property를 변경할 수 있습니다. property값을 변경하는 것은 dot, bracket notation 모두 가능합니다.

```javascript
var ourDog = {
    "name": "Camper",
    "legs": 4,
    "tails": 1,
    "friends": ["everything!"]
};
```

<br>

### Add New Properties to a JavaScript Object

property를 수정하는 방법으로 이미 존재하는 object에 새로운 property를 만들 수도 있습니다. 

Here's how we would add a `"bark"`property to `ourDog`

```javascript
var ourDog = {
    "name": "Camper",
    "legs": 4,
    "tails": 1,
    "friends": ["everything!"]
};

ourDog.bark = "bow-wow";
```

<br>

### Delete Properties from a JavaScript Object

object로부터 property를 제거할 수도 있습니다.

```javascript
var ourDog = {
    "name": "Camper",
    "legs": 4,
    "tails": 1,
    "friends": ["everything!"],
    "bark": "bow-wow"
};

delete ourDog.bark
```

<br>

### Using Objects for Lookups

object는 key/value 형태의 일종의 사전으로 해석될 수 있습니다. 표 형태의 데이터를 저장하고자 할때, `if/else` 문이나 `switch` 문말고 object를 사용할 수도 있습니다. This is most useful when you know that your input data is limited to a certain range.

```javascript
var alpha = {
    1:"Z",
    2:"Y",
    3:"X",
    4:"W",
    ...
    24:"C",
    25:"B",
    26:"A"
};
alpha[2]; // "Y"
alpha[24]; // "C"

var value = 2;
alpha[value]; // "Y"
```

<br>

### Testing Objects for Properties

때때로 property 값이 존재하는지 알고 있을 필요가 있는데, 이때 `.hasOwnProperty(propname)` method를 사용할 수 있다. `.hasOwnProperty()` method는 `true` 아니면 `false` 값을 리턴한다.

```javascript
var myObj = {
    top: "hat",
    bottom: "pants"
};
myObj.hasOwnProperty("top"); // true
myObj.hasOwnProperty("middle"); // false
```

<br>

### Record Collection

```javascript
// Setup
var collection = {
    "2548": {
        "album": "Slippery When Wet",
        "artist": "Bon Jovi",
        "tracks": [ 
            "Let It Rock", 
            "You Give Love a Bad Name" 
        ]
    },
    "2468": {
        "album": "1999",
        "artist": "Prince",
        "tracks": [ 
            "1999", 
            "Little Red Corvette" 
        ]
    },
    "1245": {
        "artist": "Robert Palmer",
        "tracks": [ ]
    },
    "5439": {
        "album": "ABBA Gold"
    }
};
// Keep a copy of the collection for tests
var collectionCopy = JSON.parse(JSON.stringify(collection));

// Only change code below this line
function updateRecords(id, prop, value) {
    if(value == "")
    {
        delete collection[id][prop];
    }
    else{
        if(prop !== "tracks"){
            collection[id][prop] = value;
        }else{
            if(!collection[id].hasOwnProperty(prop)){
                collection[id][prop] = [];
                collection[id][prop].push(value);
            }else{
                collection[id][prop].push(value);
            }
        }
    }
    return collection;
}

// Alter values below to test your code
updateRecords(5439, "artist", "ABBA");

```

<br>

### Iterate with JavaScript While Loops

똑같은 코드를 여러번 실행하기를 원할 때,  loop를 사용합니다. 그 중 하나를 `while` loop라고 합니다. `while` loop는 특정 조건이 `true`일 때 계속 동작하며, 조건이 `true`가 더 이상 아니면 멈추게 됩니다.

```javascript
var ourArray = [];
var i = 0;
while(i < 5) {
    ourArray.push(i);
    i++;
}
```

<br>

### Iterate with JavaScript For Loops

또 다른 loop로는 `for` loop가 있습니다. `for` loop는 딱 원하는 횟수만큼 코드를 실행할 수 있는 특징이 있습니다. `for` loop는 3개의 expression으로 구성되어 있습니다.

`for ([initialization]; [condition]; [final-expression])`

The `initialization`statement is executed one time only before the loop starts. It is typically used to define and setup your loop variable.

The `condition`statement is evaluated at the beginning of every loop iteration and will continue as long as it evaluates to `true`. When `condition`is `false`at the start of the iteration, the loop will stop executing. This means if `condition`starts as `false`, your loop will never execute.

The `final-expression`is executed at the end of each loop iteration, prior to the next `condition`check and is usually used to increment or decrement your loop counter.

```javascript
var ourArray = [];
for (var i = 0; i < 5; i++) {
    ourArray.push(i);
}
```

`for` loop에서 반드시 한번에 숫자 1만큼만 더할 필요는 없습니다. `final-expression`을 바꿔 짝수만 셀 수도 있습니다.

```javascript
var ourArray = [];
for (var i = 0; i < 10; i += 2) {
    ourArray.push(i);
}
```

`for` loop는 조건만 만족시킨다면, 뒤에서 부터 숫자를 셀 수도 있습니다. In order to count backwards by twos, we'll need to change our `initialization`, `condition`, and `final-expression`.

```javascript
var ourArray = [];
for (var i=10; i > 0; i-=2) {
    ourArray.push(i);
}
```

`for` loop를 활용해 array를 Iterate할 수 있습니다.

```javascript
var arr = [10,9,8,7,6];
for (var i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

**Tip**: Remember that Arrays have zero-based numbering, which means the last index of the array is length - 1. Our condition for this loop is `i < arr.length`, which stops when `i`is at length - 1.

만약에  multi-dimensional array에 접근하고 싶다면, array와 sub-array에 모두 for문을 사용해 접근할 수 있습니다.

```javascript
var arr = [
    [1,2], [3,4], [5,6]
];
for (var i=0; i < arr.length; i++) {
    for (var j=0; j < arr[i].length; j++) {
        console.log(arr[i][j]);
    }
}
```

<br>

### Iterate with JavaScript Do...While Loops

`do...while` loop는 무조건 안쪽에 있는 코드를 1번 실행하고 그리고 `while` 조건을 검사합니다. 

```javascript
var ourArray = [];
var i = 0;
do {
    ourArray.push(i);
    i++;
} while (i < 5);
```

 `do...while` loop는 안쪽 코드를 최소 1번은 실행합니다.

<br>

### Profile Lookup

```javascript
//Setup
var contacts = [
    {
        "firstName": "Akira",
        "lastName": "Laine",
        "number": "0543236543",
        "likes": ["Pizza", "Coding", "Brownie Points"]
    },
    {
        "firstName": "Harry",
        "lastName": "Potter",
        "number": "0994372684",
        "likes": ["Hogwarts", "Magic", "Hagrid"]
    },
    {
        "firstName": "Sherlock",
        "lastName": "Holmes",
        "number": "0487345643",
        "likes": ["Intriguing Cases", "Violin"]
    },
    {
        "firstName": "Kristian",
        "lastName": "Vos",
        "number": "unknown",
        "likes": ["JavaScript", "Gaming", "Foxes"]
    }
];


function lookUpProfile(name, prop){
    // Only change code below this line
    for(var i = 0; i < contacts.length; i++){
        if(name === contacts[i].firstName){
            if(contacts[i].hasOwnProperty(prop)){
                return contacts[i][prop]
            }else{
                return "No such property"
            }
        }
    }
    return "No such contact"
    // Only change code above this line
}

// Change these values to test your function
lookUpProfile("Akira", "likes");
```

