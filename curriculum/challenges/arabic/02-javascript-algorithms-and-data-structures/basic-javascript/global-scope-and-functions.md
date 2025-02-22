---
id: 56533eb9ac21ba0edf2244be
title: النطاق الشامل والوظائف
challengeType: 1
videoUrl: 'https://scrimba.com/c/cQM7mCN'
forumTopicId: 18193
dashedName: global-scope-and-functions
---

# --description--

في JavaScript، يشير <dfn>النطاق</dfn> إلى رؤية المتغيرات. يكون إلى المتغيرات التي تم تعريفها خارج الوظيفة نطاق يسمي <dfn>شامل</dfn>. وهذا يعني أنه يمكن رؤيتها في كل مكان في التعليمات البرمجية JavaScript الخاص بك.

يتم تعريف المتغيرات دون استخدام الكلمات الآتية `let` أو `const` يتم إنشاؤها تلقائيًا في نطاق `global`. هذا يمكن أن يؤدي إلى عواقب غير مقصودة في مكان آخر من التعليمات البرمجية الخاص بك أو عند تشغيل الوظيفة مرة أخرى. يجب عليك دائماً تعريف المتغيرات الخاصة بك باستخدام `let` أو `const`.

# --instructions--

باستخدام `let` أو `const`، عرف متغير شامل يسمى `myGlobal` خارج الوظيفة ما. قم بتهيئته بقيمة `10`.

داخل الوظيفة `fun1`، عيّّن `5` إلى `oopsGlobal` ولكن ***دون*** استخدام `var`, أو `let`, أو `const`.

# --hints--

يجب أن يتم تعريف `myGlobal`

```js
assert(typeof myGlobal != 'undefined');
```

يجب أن يساوي `myGlobal` قيمة `10`

```js
assert(myGlobal === 10);
```

يجب تعريف `myGlobal` باستخدام `let` أو `const`

```js
assert(/(let|const)\s+myGlobal/.test(code));
```

يجب أن يكون متغير `oopsGlobal` شامل وأن يساوي `5`

```js
assert(typeof oopsGlobal != 'undefined' && oopsGlobal === 5);
```

# --seed--

## --before-user-code--

```js
var logOutput = "";
var originalConsole = console
function capture() {
    var nativeLog = console.log;
    console.log = function (message) {
        logOutput = message;
        if(nativeLog.apply) {
          nativeLog.apply(originalConsole, arguments);
        } else {
          var nativeMsg = Array.prototype.slice.apply(arguments).join(' ');
          nativeLog(nativeMsg);
        }
    };
}

function uncapture() {
  console.log = originalConsole.log;
}
var oopsGlobal;
capture();
```

## --after-user-code--

```js
fun1();
fun2();
uncapture();
(function() { return logOutput || "console.log never called"; })();
```

## --seed-contents--

```js
// Declare the myGlobal variable below this line


function fun1() {
  // Assign 5 to oopsGlobal Here

}

// Only change code above this line

function fun2() {
  var output = "";
  if (typeof myGlobal != "undefined") {
    output += "myGlobal: " + myGlobal;
  }
  if (typeof oopsGlobal != "undefined") {
    output += " oopsGlobal: " + oopsGlobal;
  }
  console.log(output);
}
```

# --solutions--

```js
const myGlobal = 10;

function fun1() {
  oopsGlobal = 5;
}

function fun2() {
  var output = "";
  if(typeof myGlobal != "undefined") {
    output += "myGlobal: " + myGlobal;
  }
  if(typeof oopsGlobal != "undefined") {
    output += " oopsGlobal: " + oopsGlobal;
  }
  console.log(output);
}
```
