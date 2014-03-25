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

## [`queryString`](http://stackoverflow.com/a/901144/1420197)

```js
function queryString (name) {
    name = name.replace(/[\[]/, "\\[").replace(/[\]]/, "\\]");
    var regex = new RegExp("[\\?&]" + name + "=([^&#]*)"),
        results = regex.exec(location.search);
    return results == null ? "" : decodeURIComponent(results[1].replace(/\+/g, " "));
}
```
