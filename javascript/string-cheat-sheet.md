# String Cheat Sheet

## Static Methods

### String.fromCharCode\(args...\)

Given a set of comma separeted chars, it will return a built string.

```javascript
E.g. => String.fromCharCode(75, 101, 114, 110, 101, 108) => Kernel

```

Note: You can use stuff like: `\U+000+`.

### String.fromCodePoint\(args...\)

Basically an upgraded version of `String.fromCharCode()` you can use Unicode Characters from Emoji and they will print out. 

The Unicode for 🎮 is `U+1F3AE`, in Javascript you will get this by using `0x1F3AE`. The following code _**works for**_   ****`fromCodePoint()`, but it doesn't return the emoji properly, that's why I say it's an upgraded version.

```javascript
String.fromCodePoint(0x1F3AE); => 🎮 //Unicode: 0x1F3AE
```

