utils
=====

Useful JavaScript functions.

## `eachFooWithDelay`

```js
function eachFooDelay () {
  var args  = [].splice.call(arguments,0)
    , l = args.length
    , delay = Number(args[l - 1])
    , i = -1
    ;
    
  var interval = setInterval(function () {
    if (typeof args[++i] === "function") {
      args[i]();
    } else {
      clearInterval(interval);
    }
  }, delay)
}
```

### Example

```js
eachFooDelay(
    function () {console.log(1)} 
  , function () {console.log(2)} 
  , function () {console.log(3)} 
  , function () {console.log(4)}
  , 1000
) 
```
