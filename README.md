
# johnnys-utils

 [![Patreon](https://img.shields.io/badge/Support%20me%20on-Patreon-%23e6461a.svg)][patreon] [![PayPal](https://img.shields.io/badge/%24-paypal-f39c12.svg)][paypal-donations] [![AMA](https://img.shields.io/badge/ask%20me-anything-1abc9c.svg)](https://github.com/IonicaBizau/ama) [![Version](https://img.shields.io/npm/v/johnnys-utils.svg)](https://www.npmjs.com/package/johnnys-utils) [![Downloads](https://img.shields.io/npm/dt/johnnys-utils.svg)](https://www.npmjs.com/package/johnnys-utils) [![Get help on Codementor](https://cdn.codementor.io/badges/get_help_github.svg)](https://www.codementor.io/johnnyb?utm_source=github&utm_medium=button&utm_term=johnnyb&utm_campaign=github)

> Useful JavaScript functions.

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

## :yum: How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].


## :moneybag: Donations

Another way to support the development of my open-source modules is
to [set up a recurring donation, via Patreon][patreon]. :rocket:

[PayPal donations][paypal-donations] are appreciated too! Each dollar helps.

Thanks! :heart:


## :scroll: License

[MIT][license] © [Ionică Bizău][website]

[patreon]: https://www.patreon.com/ionicabizau
[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RVXDDLKKLQRJW
[donate-now]: http://i.imgur.com/6cMbHOC.png

[license]: http://showalicense.com/?fullname=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica%40gmail.com%3E%20(http%3A%2F%2Fionicabizau.net)&year=2014#license-mit
[website]: http://ionicabizau.net
[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md
