# Define Functions in JavaScript

there are multiple ways to define functions in JS.

The most common syntax is :
```function name  (arguments){statement} ```

``` js
function calcRectArea(width, height) {
  return width * height;
}

console.log(calcRectArea(5, 9));
// expected output: 45
``` 


or the arrow notation that looks like :
``` (arguments) => {statement}```

``` js 
let area = (width, height) => {
 return width * height;
}

```

The arrow notation is more simple to define and use , but i think it can be confusing(at least for me) while defining large functions with many arguments.
The arrow notation can be more simple like the example above .


More simple way :
``` js
let area = (width, height) => widht * height 

```

References :
 - [Functions - Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
