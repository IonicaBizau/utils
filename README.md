<!-- Please do not edit this file. Edit the `blah` field in the `package.json` instead. If in doubt, open an issue. -->


# johnnys-utils

 [![Support me on Patreon][badge_patreon]][patreon] [![Buy me a book][badge_amazon]][amazon] [![PayPal][badge_paypal_donate]][paypal-donations] [![Ask me anything](https://img.shields.io/badge/ask%20me-anything-1abc9c.svg)](https://github.com/IonicaBizau/ama) [![Version](https://img.shields.io/npm/v/johnnys-utils.svg)](https://www.npmjs.com/package/johnnys-utils) [![Downloads](https://img.shields.io/npm/dt/johnnys-utils.svg)](https://www.npmjs.com/package/johnnys-utils)

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


## :sparkling_heart: Support my projects

I open-source almost everything I can, and I try to reply everyone needing help using these projects. Obviously,
this takes time. You can integrate and use these projects in your applications *for free*! You can even change the source code and redistribute (even resell it).

However, if you get some profit from this or just want to encourage me to continue creating stuff, there are few ways you can do it:

 - Starring and sharing the projects you like :rocket:
 - [![Buy me a book][badge_amazon]][amazon]—I love books! I will remember you after years if you buy me one. :grin: :book:
 - [![PayPal][badge_paypal]][paypal-donations]—You can make one-time donations via PayPal. I'll probably buy a ~~coffee~~ tea. :tea:
 - [![Support me on Patreon][badge_patreon]][patreon]—Set up a recurring monthly donation and you will get interesting news about what I'm doing (things that I don't share with everyone).
 - **Bitcoin**—You can send me bitcoins at this address (or scanning the code below): `1P9BRsmazNQcuyTxEqveUsnf5CERdq35V6`

    ![](https://i.imgur.com/z6OQI95.png)

Thanks! :heart:



## :scroll: License

[MIT][license] © [Ionică Bizău][website]

[badge_patreon]: http://ionicabizau.github.io/badges/patreon.svg
[badge_amazon]: http://ionicabizau.github.io/badges/amazon.svg
[badge_paypal]: http://ionicabizau.github.io/badges/paypal.svg
[badge_paypal_donate]: http://ionicabizau.github.io/badges/paypal_donate.svg
[patreon]: https://www.patreon.com/ionicabizau
[amazon]: http://amzn.eu/hRo9sIZ
[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RVXDDLKKLQRJW
[donate-now]: http://i.imgur.com/6cMbHOC.png

[license]: http://showalicense.com/?fullname=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica%40gmail.com%3E%20(https%3A%2F%2Fionicabizau.net)&year=2014#license-mit
[website]: https://ionicabizau.net
[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md
