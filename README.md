# johnnys-utils [![Support this project][donate-now]][paypal-donations]

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
    name = name.replace(/[\[]/, "\[").replace(/[\]]/, "\]");
    var regex = new RegExp("[\?&]" + name + "=([^&#]*)"),
        results = regex.exec(location.search);
    return results == null ? "" : decodeURIComponent(results[1].replace(/\+/g, " "));
}
```
## Convert

Convert the following structure:

```sh
$ tree
.
├── 1.html
├── 2.html
└── 3.html

0 directories, 3 files
```

into:

```sh
 tree
.
├── 1
│   ├── de.html
│   ├── fr.html
│   └── it.html
├── 2
│   ├── de.html
│   ├── fr.html
│   └── it.html
└── 3
    ├── de.html
    ├── fr.html
    └── it.html

3 directories, 9 files
```

Code:

```sh
for file in *.html; do
    echo "Copying $file"
    NAME=`node -pe 'f = process.argv[1]; f.substring(0, f.indexOf("."))' $file`
    mkdir $NAME
    cp $file $NAME/de.html
    cp $file $NAME/fr.html
    cp $file $NAME/it.html
    rm $file;
done
```

## How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].

## License

[MIT][license] © [Ionică Bizău][website]

[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RVXDDLKKLQRJW
[donate-now]: http://i.imgur.com/6cMbHOC.png

[license]: http://showalicense.com/?fullname=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica%40gmail.com%3E%20(http%3A%2F%2Fionicabizau.net)&year=2014#license-mit
[website]: http://ionicabizau.net
[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md