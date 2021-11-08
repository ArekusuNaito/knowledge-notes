# String Cheat Sheet

## Static Methods

### String.fromCharCode(args...)

Given a set of comma separeted chars, it will return a built string.

```javascript
E.g. => String.fromCharCode(75, 101, 114, 110, 101, 108) => Kernel

```

Note: You can use stuff like: `\U+000+`.

### String.fromCodePoint(args...)

Basically an upgraded version of `String.fromCharCode()` you can use Unicode Characters from Emoji and they will print out.&#x20;

The Unicode for 🎮 is `U+1F3AE`, in Javascript you will get this by using `0x1F3AE`. The following code _**works for **_**  **`fromCodePoint()`, but it doesn't return the emoji properly, that's why I say it's an upgraded version.

Note: This was introduced in ES6.

```javascript
String.fromCodePoint(0x1F3AE); => 🎮 //Unicode: 0x1F3AE
```

## Instance Methods / Properties

If you wanna know what a `"kernel".something() `does, these are the methods you are looking for.

### .length

If you wanna know the size of a string. This is what you are looking for.

```javascript
"Kernel".length => 6 ,  "Nintendo".length => 8
```

### .charAt(position:number)

If you wanna know what character is at an specific position of your string. Negative numbers are not usable.

```javascript
"Dog".charAt(0) => 'D' 
```

You can also use a short-hand similar to other languages. Remember that strings are basically a string/collection of characters chained together.

```javascript
"Dog"[0] => 'D'
```

### .charCodeAt(position:number)

If you wanna know what is the _Character Code _from a string, you can get it.

```javascript
// What's the character code for: N?
"Nintendo".charCodeAt(0) =>
```

Note: The "inverse" function to get character given a code (number)  would be: [String.fromCharCode(args)](string-cheat-sheet.md#string-fromcharcode-args)

### .codePointAt(position:number)

Very similar to [`charCodeAt(position:number)`](string-cheat-sheet.md#charcodeat-position-number) however, it will normally be used for emojis/icons or very special and unique characters.

```javascript
'🎮💻'.codePoint(0) =>//127918: Which is 🎮's char Code
```

Note: The "inverse" function to get character given a code (number)  would be: [String.fromCodePoint(args)](string-cheat-sheet.md#string-fromcodepoint-args)

### .concat(anotherString, \[...moreStrings] )

This is a "long-hand" version of using the `+` operator. With this function you will combine/fusion strings. For example if you have three strings like:

1. Chocolate
2. Cake

And you want to add them up, you can use the function like this:

```javascript
const chocoString = "Chocolate"
const cakeString = "Cake"
const chocoCake = chocoString.concat(cakeString); 
console.log(chocoCake); => "ChocolateCake"
```

Notice how we are missing a space, because the _"Space"_  is also a special character that needs to be added up. The Mozilla javascript reference, strongly recommends to use the `+` operator instead of using the `concat(anotherString:string, [...moreStrings])` function.

Here's an example:

```javascript
const chocoString = "Chocolate"
const cakeString = "Cake"
const chocoCake = chocoString+" "+cakeString;
console.log(chocoCake); => "Chocolate Cake"
```

Notice how this has more legibility and we easily added that extra space.

I found an extra special thing, if you have an array of strings, you can just use the spread operator (`...`) to `reduce` them to a single string.

```javascript
const manyWords = ["Kirby","of","the","Stars"]

console.log(...manyWords); // => Kirby of the Stars
```

### .includes(stringYouLookingFor:string, positionToStartLooking:number)

Do you wanna know if a word is inside a paragraph, or just string of any size? You can do it with this function.&#x20;

Note: This is case-sensitive. You can transform to lower or upper case to cut-corners.

```javascript
const paragraphOne = "Kirby likes to eat Tomatoes";
const paragraphTwo = "KirbylikestoeatTomatoes";
console.log( paragraphOne.includes('eat') ); //=>true
console.log( paragraphOne.includes('EaT') ); //=>false: This is case-sensitive.
//Considering paragraph 2
console.log( paragraphTwo.includes('eat') ); //=>true
console.log( paragraphTwo.includes('EaT') ); //=>false: This is case-sensitive.
//
console.log( paragraphOne.includes("Kirby",1)  ); //=>False
console.log( paragraphOne.includes("Kirby",0)  ); //=>True
//
"".includes("") // =>True. I believe this just means that this string exists, even if its empty


```

### .endsWith(stringYouLookingFor:string, length:number)

If you wanna check for a string to end with an specific string you can use this one. For example, a question.

```javascript
const sentence = "Dogs are cute";
console.log( sentence.endsWith('?') ) //=>false

console.log( sentence.endsWith('Dogs') ) //=>false
console.log( sentence.endsWith('Cute') ) //=>false, case-sensitive
console.log( sentence.endsWith('cute') ) //=>true ✔

//
console.log(sentence.endsWith('D',1) ); //=>true ✔
console.log(sentence.endsWith('o',2) ); //=>true ✔
console.log(sentence.endsWith('g',3) ); //=>true ✔
console.log(sentence.endsWith('s',4) ); //=>true ✔


```

### .indexOf(stringYouLookingFor:string,position:number)

In a way, it is useful like the `.includes()` method. But this one will return the `index/position` in the string, which, don't forget is an `array` of characters.

```javascript
const sentence = "Dogs want to eat Hot Dogs 🌭";
console.log( sentence.indexOf('?') ) //=>-1 : Not Found

console.log( sentence.indexOf('Dogs') ) //=> 0
console.log( sentence.indexOf('Cute') ) //=> -1
console.log( sentence.indexOf('cute') ) //=> 9

//
console.log(sentence.indexOf('D',0) ); //=> 0
console.log(sentence.indexOf('o',1) ); //=> 1
console.log(sentence.indexOf('g',2) ); //=> 2
console.log(sentence.indexOf('s',3) ); //=> 3
```



### .lastIndexOf(stringYouAreLookingFor:string, positionWhereToStartSearch:number)

The opposite of `indexOf` as we start looking for the given input in backwards order.

_Notes: Second Argument \~ Optional. The position where to start the search (searching backwards). If omitted, the default value is the length of the string. In other words: We ignore everything to the right of the index argument. Still look backwards._

```javascript
const sentence = "Dogs want to eat Hot Dogs 🌭";
//Apparently emojis are not length 1? but they have a bigger length size.
console.log(`Sentence length: ${sentence.length}`);
console.log( sentence.lastIndexOf('D') ) //=>- 21 : The first D, starting from the end
console.log( sentence.lastIndexOf('🌭') ) //=> 26

console.log( sentence.lastIndexOf('Dogs') ) //=> 21 //We should be getting the second "Dogs" ✔
console.log( sentence.lastIndexOf('Cats') ) //=> -1 //This is not even in the sentence

// Second Argument"
//Optional. The position where to start the search (searching backwards). 
//If omitted, the default value is the length of the string.
//In other words: We ignore everything to the right of the index argument. Still look backwards.
console.log('want',sentence.lastIndexOf('w',4) ); //=> 3

console.log();
console.log('For Tenebrae')
//T [e] n [e] b r a [e]
//0 1  2  3  4 5 6  7
console.log('Tenebrae','Tenebrae'.lastIndexOf('e') ); //=>7
console.log('Tenebrae 0','Tenebrae'.lastIndexOf('e',0) ); //=> -1
console.log('Tenebrae 1','Tenebrae'.lastIndexOf('e',1) ); //=>  1
console.log('Tenebrae 2','Tenebrae'.lastIndexOf('e',2) ); //=>  1
console.log('Tenebrae 3','Tenebrae'.lastIndexOf('e',3) ); //=>  3
console.log('Tenebrae 4','Tenebrae'.lastIndexOf('e',4) ); //=>  3
console.log('Tenebrae 5','Tenebrae'.lastIndexOf('e',5) ); //=>  3
console.log('Tenebrae 6','Tenebrae'.lastIndexOf('e',6) ); //=>  3
console.log('Tenebrae 7','Tenebrae'.lastIndexOf('e',7) ); //=> 7
```

### .localeCompare(stringComparedAgainst:string,  ...locales,options)

To further research. From what I get, this will help to compare strings between diferent languages. And it will tell you whether if its before or after regarding the sorting on character codes.

Note: As the creation of this document, not all options are available in all browsers, and I won't write them becuase of that.

```javascript
const a = 'réservé'; // with accents, lowercase
const b = 'RESERVE'; // no accents, uppercase

console.log(a.localeCompare(b));
// expected output: 1
console.log(a.localeCompare(b, 'en', { sensitivity: 'base' }));
// expected output: 0
```



### .trim()

This removes white-spaces from the ends of a string. This should not remove whitespaces between characters.



### .replace()

This returns a new string given a `pattern/regular expression` given.&#x20;

```javascript
const sentence = "Cats are Awesome!, Cats are Cool!";
const newSentence = sentence.replace('Cats','Dogs');
const regexSentence = sentence.replace(/Cats/g,'Lions')
console.log('Old Sentence',sentence)
console.log('New Sentence',newSentence)
console.log('Regex Sentence',regexSentence);
```

### .slice(startPosition:number,endPosition:number)

Extracts a `slice` or portion of a string, you will end up with a `substring` of the original string. Imagine that you are getting a slice of the whole cake 🎂.

```javascript
const sentence = "Dogs are Awesome!, Dogs are Cool!";
const wordToLook = "Awesome";
const wordIndex = sentence.search(wordToLook);
const sliceString = sentence.slice(wordIndex,wordIndex+wordToLook.length);
console.log(sliceString);
```

### .split(separator:string)

Splits the string into an array given a separator. For example, when you want to get the words from a sentence, or you want the individual characters of a word.

Note: The separator is not neccesarily a `char` it can be a string. you could `split('foo')` if you want.

```javascript
const sentence = "Samus Aran shoots lasers";
const words = sentence.split('');
console.log(words);
const characters = sentence.split('');
console.log(characters)

console.log(words.join('-'));
```

### substr(positionToStart:number,numOfCharactersToInclude:number)

Similar to slice. You can find and get a slice/substring giving an `index/position` and how many characters you want after that. Personally this one makes a lot of sense to be the actual slice function.

```javascript
const sentence = "Dogs are cool and awesome!";
const wordToSearch = "and";
const index = sentence.indexOf(wordToSearch);
const foundWord = sentence.substr(index,wordToSearch.length);

console.log(foundWord)

```
