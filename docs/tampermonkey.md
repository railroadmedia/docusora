
Tampermonkey Helpful Environment-Differentiation of Environments to Against Destructive Actions on Production Please. (T.H.E.D.E.A.D.A.P.P.)
==========================

See different environments in different colours so you don't accidentally go buck-wild on prod when you meant to be deleting and spamming everything you can see on staging or local instead.


***NOTE**: The above examples are for the old CMS, they won't work with the new one. Feel free to update them and delete this comment.*


Instructions
-------------------------

1. Install [TamperMonkey](https://tampermonkey.net/)
2. Copy-pasta the code below to create scripts
3. Get 'em working


Scripts
-------------------------

### Local — GREEN

```
// ==UserScript==
// @name         musora dev marker
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  make it so you don't fuck around on prod when you mean to actually fuck around on local
// @author       You

// @match        *dev.musora.com/*

// @grant        none
// ==/UserScript==

(function() {
    'use strict';
    // Your code here...
    function addGlobalStyle(css) {
        var head, style;
        head = document.getElementsByTagName('head')[0];
        if (!head) { return; }
        style = document.createElement('style');
        style.type = 'text/css';
        style.innerHTML = css;
        head.appendChild(style);
    }

    // dev
    addGlobalStyle('body{background:#96FF96}');
    addGlobalStyle('.top-bar, .content-side-bar{background:#4B7F4B};');

    // staging
    //addGlobalStyle('body{background:#E5FF96};');
    //addGlobalStyle('.top-bar, .content-side-bar{background:#727F4B};');

    // prod
    //addGlobalStyle('body{background:#FF9696};');
    //addGlobalStyle('.top-bar, .content-side-bar{background:#7F4B4B};');

    // end of your code here.
})();
```

### Staging — YELLOW

```
// ==UserScript==
// @name         musora staging marker
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  make it so you don't fuck around on prod when you mean to actually fuck around on local
// @author       You

// @match        https://staging.musora.com/*

// @grant        none
// ==/UserScript==

(function() {
    'use strict';
    // Your code here...
    function addGlobalStyle(css) {kthxbie
        var head, style;
        head = document.getElementsByTagName('head')[0];
        if (!head) { return; }
        style = document.createElement('style');
        style.type = 'text/css';
        style.innerHTML = css;
        head.appendChild(style);
    }

    // dev
    //addGlobalStyle('body{background:#96FF96}');
    //addGlobalStyle('.top-bar, .content-side-bar{background:#4B7F4B};');

    // staging
    addGlobalStyle('body{background:#E5FF96};');
    addGlobalStyle('.top-bar, .content-side-bar{background:#727F4B};');

    // prod
    //addGlobalStyle('body{background:#FF9696};');
    //addGlobalStyle('.top-bar, .content-side-bar{background:#7F4B4B};');

    // end of your code here.
})();
```

### Production — RED

```
// ==UserScript==
// @name         musora prod marker
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  make it so you don't fuck around on prod when you mean to actually fuck around on local
// @author       You

// @match        https://www.musora.com/*

// @grant        none
// ==/UserScript==

(function() {
    'use strict';
    // Your code here...
    function addGlobalStyle(css) {
        var head, style;
        head = document.getElementsByTagName('head')[0];
        if (!head) { return; }
        style = document.createElement('style');
        style.type = 'text/css';
        style.innerHTML = css;
        head.appendChild(style);
    }

    // dev
    //addGlobalStyle('body{background:#96FF96}');
    //addGlobalStyle('.top-bar, .content-side-bar{background:#4B7F4B};');

    // staging
    //addGlobalStyle('body{background:#E5FF96};');
    //addGlobalStyle('.top-bar, .content-side-bar{background:#727F4B};');

    // prod
    addGlobalStyle('body{background:#FF9696};');
    addGlobalStyle('.top-bar, .content-side-bar{background:#7F4B4B};');

    // end of your code here.
})();
```


