# Conditions in JavaScript
if something , do something.

The syntax to use conditions is JavaScript :

``` js
if (condition) {
  statement1
} else {
  statement2
}
```
``` js
function testNum(a) {
  let result;
  if (a > 0) {
    result = 'positive';
  } else {
    result = 'NOT positive';
  }
  return result;
}

console.log(testNum(-5));
// expected output: "NOT positive"
```

References :
 - [if...-else - Javascript](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Statements/if...else)
