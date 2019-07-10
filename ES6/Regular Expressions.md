# Regular Expressions

Regular expressions are special strings that represent a search pattern. Also known as "regex" or "regexp", they help programmers match, search, and replace text. Regular expressions can appear cryptic because a few characters have special meaning. The goal is to combine the symbols and text into a pattern that matches what you want, but only what you want. This section will cover the characters, a few shortcuts, and the common uses for writing regular expressions.

<br>

### Using the Test Method

Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching. 만약 `"The dog chased the cat"` 에서 `"the"` 를 찾고 싶으면 `/the/` 이와 같은 정규 표현식을 사용할 수 있습니다. 정규표현식에서는 quotes를 문자열에 사용하지 않습니다.

자바스크립트는 regexes를 사용하는 여러 방법을 가지고 있습니다. 하나는 `.test()` method를 사용해 regex를 테스트하는 방법입니다. `.test()` method는 regex를 가져와 문자열에 적용시켜 그 pattern을 찾으면 `true`를 못 찾으면 `false`를 return합니다.

```javascript
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr);
// Returns true
```

<br>

### Match Literal Strings

```javascript
let testStr = "Hello, my name is Kevin.";
let testRegex = /Kevin/;
testRegex.test(testStr);
// Returns true
```

위코드에서 오직 `/Kevin/` 만이 match되고 `/kevin/` 이나 `/KEVIN/`은 match되지 않습니다.

```javascript
let testStr = "Hello, my name is Kevin.";
let wrongRegex = /kevin/;
wrongRegex.test(testStr);
// Returns false
```

<br>

### Match a Literal String with Different Possibilities

`/coding/` 정규 표현식을 통해 문자열에서 `"coding"` 패턴을 찾을 수 있습니다. 이는 하나의 문자열을 찾는데는 매우 유용하지만 한가지 pattern에 국한되어 있습니다. 따라서 여러개의 pattern을 찾으려면 `alternation` 이나 `OR` 연산자인 `|`을 활용해 찾을 수 있습니다. This operator matches patterns either before or after it. For example, if you wanted to match `"yes"`or `"no"`, the regex you want is `/yes|no/`. 두개 이상의 pattern도 찾아낼 수 있습니다. `OR` 연산자를 통해 분리시켜 추가할 수 있습니다 (`/yes|no|maybe/`).

<br>

### Ignore Case While Matching

지금까지 문자열을 그대로 match되는 것을 정규표현식으로 해봤습니다. 이번에는 case가 달라도 match되는 방법을 배워보겠습니다.

Case는 uppercase와 lowercase로 나누어집니다. uppercase는 "A", "B", "C"이며 lowercase는 "a", "b", "c" 입니다. flag를 활용해 2가지 case에 상관없이 match되게끔 만들 수 있습니다. 많은 flag가 존재하지만 여기서는 `i` flag를 활용하겠습니다. 정규식 뒷부분에 이를 추가해서 사용할 수 있습니다.

```javascript
/ignorecase/i
```

위 정규식은 `"ignorecase"`, `"igNoreCase"`, and `"IgnoreCase"`와 모두 match됩니다.

<br>

### Extract Matches

지금까지 정규 표현식을 활용해 특정 패턴이 문자열안에 있는지 없는지를 체크했습니다. 실제로 특정 패턴을 `.match()` method를 활용해 추출할 수 있습니다.

```javascript
"Hello, World!".match(/Hello/);
// Returns ["Hello"]
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);
// Returns ["expressions"]
```

<br>

### Find More Than the First Match

바로 전, 특정 pattern을 한번만 찾아 추출하는 것을 배웠습니다.

```javascript
let testStr = "Repeat, Repeat, Repeat";
let ourRegex = /Repeat/;
testStr.match(ourRegex);
// Returns ["Repeat"]
```

패턴을 1개 이상 찾거나 추출하기 위해서 우리는 `g` flag를 사용할 수 있습니다.

```javascript
let testStr = "Repeat, Repeat, Repeat";
let repeatRegex = /Repeat/g;
testStr.match(repeatRegex);
// Returns ["Repeat", "Repeat", "Repeat"]
```

**Tip**: You can have multiple flags on your regex like `/search/gi`

<br>

### Match Anything with Wildcard Period

Sometimes you won't (or don't need to) know the exact characters in your patterns. Thinking of all words that match, say, a misspelling would take a long time. Luckily, you can save time using the wildcard character: `.`

The wildcard character `.`will match any one character. The wildcard is also called `dot`and `period`. You can use the wildcard character just like any other character in the regex. For example, if you wanted to match `"hug"`, `"huh"`, `"hut"`, and `"hum"`, you can use the regex `/hu./`to match all four words.

```javascript
let humStr = "I'll hum a song";
let hugStr = "Bear hug";
let huRegex = /hu./;
humStr.match(huRegex); // Returns ["hum"]
hugStr.match(huRegex); // Returns ["hug"]
```

<br>

### Match Single Character with Multiple Possibilities

You learned how to match literal patterns (`/literal/`) and wildcard character (`/./`). Those are the extremes of regular expressions, where one finds exact matches and the other matches everything. There are options that are a balance between the two extremes.

You can search for a literal pattern with some flexibility with `character classes`. Character classes allow you to define a group of characters you wish to match by placing them inside square (`[`and `]`) brackets.

For example, you want to match `"bag"`, `"big"`, and `"bug"`but not `"bog"`. You can create the regex `/b[aiu]g/`to do this. The `[aiu]`is the character class that will only match the characters `"a"`, `"i"`, or `"u"`.

```javascript
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex); // Returns ["big"]
bagStr.match(bgRegex); // Returns ["bag"]
bugStr.match(bgRegex); // Returns ["bug"]
bogStr.match(bgRegex); // Returns null
```

```javascript
// find all vowels
let quoteSample = "Beware of bugs in the above code; I have only proved it correct, not tried it.";
let vowelRegex = /[aeiou]/gi; 
let result = quoteSample.match(vowelRegex);
```

<br>

### Match Letters of the Alphabet

You saw how you can use `character sets`to specify a group of characters to match, but that's a lot of typing when you need to match a large range of characters (for example, every letter in the alphabet). Fortunately, there is a built-in feature that makes this short and simple.

Inside a `character set`, you can define a range of characters to match using a `hyphen`character: `-`.

For example, to match lowercase letters `a`through `e`you would use `[a-e]`.

```javascript
let catStr = "cat";
let batStr = "bat";
let matStr = "mat";
let bgRegex = /[a-e]at/;
catStr.match(bgRegex); // Returns ["cat"]
batStr.match(bgRegex); // Returns ["bat"]
matStr.match(bgRegex); // Returns null
```

```javascript
let quoteSample = "The quick brown fox jumps over the lazy dog.";
let alphabetRegex = /[a-z]/gi; 
let result = quoteSample.match(alphabetRegex); 
```

<br>

### Match Numbers and Letters of the Alphabet

Using the hyphen (`-`) to match a range of characters is not limited to letters. It also works to match a range of numbers.

For example, `/[0-5]/`matches any number between `0`and `5`, including the `0`and `5`.

Also, it is possible to combine a range of letters and numbers in a single character set.

```javascript
let jennyStr = "Jenny8675309";
let myRegex = /[a-z0-9]/ig;
// matches all letters and numbers in jennyStr
jennyStr.match(myRegex);
```

<br>

### Match Single Characters Not Specified

So far, you have created a set of characters that you want to match, but you could also create a set of characters that you do not want to match. These types of character sets are called `negated character sets`.

To create a `negated character set`, you place a `caret`character (`^`) after the opening bracket and before the characters you do not want to match.

For example, `/[^aeiou]/gi`matches all characters that are not a vowel. Note that characters like `.`, `!`, `[`, `@`, `/`and white space are matched - the negated vowel character set only excludes the vowel characters.

```javascript
let quoteSample = "3 blind mice.";
let myRegex = /[^0-9aeiou]/gi;
let result = quoteSample.match(myRegex);
```

<br>

### Match Characters that Occur One or More Times

Sometimes, you need to match a character (or group of characters) that appears one or more times in a row. This means it occurs at least once, and may be repeated.

You can use the `+`character to check if that is the case. Remember, the character or pattern has to be present consecutively. That is, the character has to repeat one after the other.

For example, `/a+/g`would find one match in `"abc"`and return `["a"]`. Because of the `+`, it would also find a single match in `"aabc"`and return `["aa"]`.

If it were instead checking the string `"abab"`, it would find two matches and return `["a", "a"]`because the `a`characters are not in a row - there is a `b`between them. Finally, since there is no `"a"`in the string `"bcd"`, it wouldn't find a match.

```javascript
let difficultSpelling = "Mississippi";
let myRegex = /s+/gi;
let result = difficultSpelling.match(myRegex);
```

<br>

### Match Characters that Occur Zero or More Times

The last challenge used the plus `+`sign to look for characters that occur one or more times. There's also an option that matches characters that occur zero or more times.

The character to do this is the `asterisk`or `star`: `*`.

```javascript
let soccerWord = "gooooooooal!";
let gPhrase = "gut feeling";
let oPhrase = "over the moon";
let goRegex = /go*/;
soccerWord.match(goRegex); // Returns ["goooooooo"]
gPhrase.match(goRegex); // Returns ["g"]
oPhrase.match(goRegex); // Returns null
```

```javascript
let chewieQuote = "Aaaaaaaaaaaaaaaarrrgh!";
let chewieRegex = /Aa*/;
let result = chewieQuote.match(chewieRegex);
```

<br>

### Find Characters with Lazy Matching

In regular expressions, a `greedy`match finds the longest possible part of a string that fits the regex pattern and returns it as a match. The alternative is called a `lazy`match, which finds the smallest possible part of the string that satisfies the regex pattern.

You can apply the regex `/t[a-z]*i/`to the string `"titanic"`. This regex is basically a pattern that starts with `t`, ends with `i`, and has some letters in between.

Regular expressions are by default `greedy`, so the match would return `["titani"]`. It finds the largest sub-string possible to fit the pattern.

However, you can use the `?`character to change it to `lazy`matching. `"titanic"`matched against the adjusted regex of `/t[a-z]*?i/`returns `["ti"]`.

```javascript
let text = "<h1>Winter is coming</h1>";
let myRegex = /<h[a-z]*?1>/;
let result = text.match(myRegex);
```

