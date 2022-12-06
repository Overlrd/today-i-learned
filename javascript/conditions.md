#Conditions in JavaScript
if something , do something.

The syntax to use conditions is JavaScript :

```
if (condition) {
  statement1
} else {
  statement2
}
```

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
