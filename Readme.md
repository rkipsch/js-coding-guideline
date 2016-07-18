# JavaScript Coding and Style Guide

## Table of Contents

1. [Introduction](#introduction)
1. [General](#general)
  * [Code should be easy to understand](#code-should-be-easy-to-understand)
  * [Avoid common Mistakes](#avoid-common-mistakes)
  * [JSHint](#jshint)
1. [JavaScript Language Rules](#javascript-language-rules)
  * [Variable declaration](#variable-declaration)
  * [Constants](#constants)
  * [Naming](#naming)
  * [Semicolons](#semicolons)
  * [Naming `this` in nested functions](#naming-this-in-nested-functions)
  * [Function declarations within blocks or loops](#function-declarations-within-blocks-or-loops)
  * [Exceptions](#exceptions)
  * [Standard features](#standard-features)
  * [Wrapper objects for primitive types - Array and Object literals](#wrapper-objects-for-primitive-types-array-and-object-literals)
  * [Function and property definitions](#function-and-property-definitions)
  * [Function parameter](#function-parameter)
  * [eval Statement](#eval-statement)
  * [with Statement](#with-statement)
  * [try Statement](#try-tatement)
  * [switch Statement](#switch-statement)
  * [for-in loop](#for-in-loop)
  * [Array functions](#array-functions)
  * [Associative Arrays](#associative-arrays)
  * [Enumerations and constants](#enumerations-and-constants)
  * [Multiline string literals](#multiline-string-literals)
  * [Conditional expressions](#conditional-expressions)
  * [Type detection](#type-detection)
  * [Ternary operators](#ternary-operators)
  * [Shortcut expression](#shortcut-expression)
  * [Coercing](#coercing)
1. [JavaScript Style Rules](#javascript-style-rules)
  * [Intendation](#intendation)
  * [Line length](#line-length)
  * [Strings](#strings)
  * [Parentheses](#parentheses)
  * [Braces & Blocks](#braces-and-blocks)
  * [Whitespace](#whitespace)
  * [Commas](#commas)
  * [Formatting AMD modules](#formatting-amd-modules)
  * [Comments](#comments)
1. [jQuery](#jquery)
1. [JSON Style Guide](#json-style-guide)
  * [Property Name Guidelines](#property-name-guidelines)
  * [Double Quotes](#double-quotes)
  * [Formatting](#formatting)
1. [CSS Style Guide](#css-style-guide)
  * [General Coding Principles](#general-coding-principles)
  * [Naming Conventions for Selectors](#naming-conventions-for-selectors)
  * [Type Selectors](#type-selectors)
  * [0 and Units](#0-and-units)
  * [Spaces](#spaces)
1. [HTML Style Guide](#html-style-guide)
  * [General Markup Guidelines](#general-markup-guidelines)
  * [Doctype](#doctype)
  * [Formatting & Style](#formatting-and-style)
  * [Character Encoding](#character-encoding)
  * [Markup Comments](#markup-comments)
1. [License](#license)


## Introduction
The following style guide is based on other popular style guides out there and based on some best practices. The following guides have been a source of inspiration:

* http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml
* http://www.2ality.com/2013/07/meta-style-guide.html
* https://github.com/airbnb/javascript
* http://javascript.crockford.com/code.
* http://sideeffect.kr/popularconvention/
* http://isobar-idev.github.io/code-standards/
* http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference

## General

### Code should be easy to understand
> For most code, the time used for reading it is much greater than the time used for writing it. It is thus important to make the former as easy as possible


### Avoid common Mistakes
There are some common mistakes that happen here and there which should be avoided. So please follow these simple rules:
* Don't use global variables
* Use semicolons
* Don't use `==` use `===` instead
* Don't use type wrapper objects
* Don't use `with` or `eval`
* Use a radix when using `parseInt`
* Use braces on `if`-statements, `while`-statements and `for`-loops
These rules are covered also within this style guide in more detail.

A more detailed explanation of common mistakes can be found here:<br>
http://net.tutsplus.com/tutorials/javascript-ajax/the-10-javascript-mistakes-youre-making/?search_index=3

**[back to top](#table-of-contents)**


### JSHint
In order to check for certain style violations in the code, use JSHint. This helps to evaluate the code while writing it and will give you hints about some mistakes so you can easily fix them.

If you want to use it, create a file called `.jshintrc` and put it in your project root folder. Put the following settings there (and extend it even further in case):
```javascript
{
    "camelcase": true,
    "curly": true,
    "eqeqeq": true,
    "forin": true,
    "immed": true,
    "latedef": true,
    "newcap": true,
    "noarg": true,
    "noempty": true,
    "quotmark": "double",
    "undef": true,
    "unused": true,
    "strict": true,
    "trailing": true,
    "maxcomplexity": 10,
    "maxlen": 100,
    "browser": true,
    "jquery": true,
    "withstmt": false,
    "white": true,
    "indent": 4,
    "globals": {
        "requirejs": false,
        "require": false,
        "define": false,
        "window": false,
    }
}
```
Then use a JSHint plugin for your editor for instance like "SublimeLinter" for SublimeText 2 that will help you to mark your code according style violations. The rules above can be looked up here http://www.jshint.com/docs/options of the JSHint documentation (http://www.jshint.com/docs).

**[back to top](#table-of-contents)**


## JavaScript Language Rules

### Variable declaration
Declarations with `var` always.

Decision:
When you fail to specify var, the variable gets placed in the global context, potentially clobbering existing values. Also, if there's no declaration, it's hard to tell in what scope a variable lives (e.g., it could be in the Document or Window just as easily as in the local scope). So always declare with var.

Use of global variables should be avoided if possible. Implied global variables should never be used.

One variable declaration per line. Don&#8217;t declare multiple variables with a single declaration.

**Bad:**
```javascript
var foo = 3,
    bar = 2,
    baz;
```

**Good:**
```javascript
var foo = 3;
var bar = 2;
var baz;
```
Advantages: deleting, inserting and re-arranging lines is simpler and the lines are automatically indented correctly.

### Constants
Use upper case names like: `NAMES_LIKE_THIS` for constant values.


### Naming
Choose always meaningful names for files, functions, objects, variables etc.
Humans read tokens, not characters. Therefore, `redBalloon` is easier to read than `rdBlln`. Avoid single letter names.

Only objects where you create instances from are written with first upper case letter in JavaScript. Everything else is written in lower case letters. Use camelCase when naming objects, variables, functions, and instances.

**Bad:**
```javascript
var OBJEcttsssss = {};
var this_is_my_object = {};
var this-is-my-object = {};

function c () {};

var u = new user({
    name: "John Doe"
});
```


**Good:**
```javascript
var thisIsMyObject = {};

function thisIsMyFunction () {};

var user = new User({
    name: "John Doe"
});
```

Use PascalCase when naming constructors or class like objects.

**Bad:**
```javascript
function user(options) {
    this.name = options.name;
}

var bad = new user({
    name: "nope"
});
```

**Good:**
```javascript
function User(options) {
    this.name = options.name;
}

var good = new User({
    name: "John"
});
```

Since JavaScript is a loosely typed language it does not make much sense to add a prefix to the variable name to indicate it's type. Choose rather more meaningful names instead:

**Bad:**
```javascript
var strPropertyName = "foo";
var propertyValueString = "bar";
var nCounter = 1;
var iValue = 1;
var bVisible = true;
```

**Good:**
```javascript
var propertyName = "foo";
var counter = 1;
var value = 1;
var isVisible = true;
var hasModel = true;
```

This also applies for naming functions that return boolean value:
```javascript
function hasChildren () {};
function isEnabled () {};
```


AMD module example:
```javascript
define("myModule", [
    "jQuery",
    "marionette"
], function ($, Marionette) {

    "use strict";

    var View = Marionette.ItemView.extend({

        initialize: function () {
            //...
        },

        onShow: function () {
            //...
        }
    });

    return View;
});
```

Use a leading underscore _ when naming private properties or functions to visually indicate the privacy although this does not actually provide privacy.

**Bad:**
```javascript
this.__firstName__ = "Panda";
this.firstName_ = "Panda";
```
**Good:**
```javascript
this._firstName = "Panda";
```


### Semicolons
Always use semicolons.

Relying on implicit insertion can cause subtle, hard to debug problems. Don't do it.

Semicolons should be included at the end of function expressions:
```javascript
var foo = function() {
    return true;
};  // semicolon here.
```


### Naming `this` in nested functions
In case you need to store the scope of `this` temporarily into a variable in order to access it from within a nested function, prefere naming it `self` over others. `self` is visually more distinguishable than `_this` or `that` and also more meaningful.

**Bad:**
```javascript
var _this = this;
viewer.onMove(function () {
    _this.setActiveViewer();
});

var that = this;
viewer.onMove(function () {
    that.setActiveViewer();
});

var me = this;
viewer.onMove(function () {
    me.setActiveViewer();
});
```
**Good:**
```javascript
var self = this;
viewer.onMove(function () {
    self.setActiveViewer();
});
```
**Better:**
```javascript
viewer.onMove(function () {
    this.setActiveViewer();
}.bind(this));
```

Passing `this` as parameter:
```javascript
myArray.forEach(function (item) {
    //...
}, this);
```

Binding `this` to callback functions:
```javascript
Manager.onAdd(this._handleSelection.bind(this));
Manager.onRemove(this._handleDeselection.bind(this));
```


### Function declarations within blocks or loops
**No, do not do this:**
```javascript
if (x) {
    function foo() {}
}
```

**Instead** use a variable initialized with a function expression to define a function within a block:

```javascript
if (x) {
    var foo = function () {};
}
```
Also do not create functions within a loop. See here for details: http://jslinterrors.com/dont-make-functions-within-a-loop

### Exceptions
When throwing exceptions, always throw instances of `Error` or subclasses of it.


### Standard features
Always preferred over non-standard features.

For maximum portability and compatibility, always prefer standard features over non-standard features (e.g., `string.charAt(3)` over `string[3]` and element access with DOM functions instead of using an application-specific shorthand).


### Wrapper objects for primitive types - Array and Object literals
No, there's no reason to use wrapper objects for primitive types, plus they're dangerous.

Prefer literals to constructors. Several literals produce objects that can also be created by constructors. However, the latter is normally the better choice:

**Bad:**
```javascript
var obj = new Object();

var arr = new Array();
var arr = new Array("a", "b", "c");

var regex = new RegExp("abc"); // avoid if possible

var isDefault = new Boolean(true);

var myName = new String("John");
```

**Instead:**
```javascript
var obj = {};

var arr = [];
var arr = ["a", "b", "c"];

var regex = /abc/;

var isDefault = true;

var myName = "John";
```


### Function and property definitions
While there are several ways to attach function and properties to an object created via "new", the preferred way is to attach it to the prototype of the object:
```javascript
Foo.prototype.bar = function() {
    //...
};
```
The preferred way for other properties is to initialize the field in the constructor:
```javascript
function Foo() {
    this.bar = value;
}
```

Why?<br>
Current JavaScript engines optimize based on the "shape" of an object, adding a property to an object (including overriding a value set on the prototype) changes the shape and can degrade performance.


### Function parameter
In order to improve flexibility and readability of functions, it's recommended to pass an object literal rather than a list of values.

This helps to understand what are those values especially when passing multiple booleans or numbers. It also avoids breaking and changing functions when refactoring the order, removing or adding new parameter.

**Bad:**
```javascript
new MyPropertyInfo(propertyName, 2, true, true, "/my/path/");
```
**Good:**
```javascript
new MyPropertyInfo({
    name: propertyName,
    behaviorType: 2,
    isPersistent: true,
    isVisible: true,
    path: "/my/path/"
});
```


### eval Statement
`eval()` is evil. Never use eval!


### with Statement
No, don't use `with`. Furthermore it's deprecated.


### try Statement

The try class of statements should have the following form:
```javascript
try {
    statements
} catch (variable) {
    statements
}

try {
    statements
} catch (variable) {
    statements
} finally {
    statements
}
```


### switch Statement
```javascript
switch (x) {
case 0:
    // ...
    break;
case 1:
    // ...
    break;
default:
    // ...
    break;
}
```


### for-in loop
for-in loops are often incorrectly used to loop over the elements in an Array. This is however very error prone because it does not loop from 0 to length - 1 but over all the present keys in the object and its prototype chain.

Therefore avoid using for-in loops.

if you want to iterate over an object literal, you can use the following approach:
```javascript
Object.keys(obj).forEach(function(key) {
    var value = obj[key];
});
```


### Array functions
Because functions are first-class objects, we can pass a function as an argument in another function and later execute that passed-in function or even return it to be executed later. This is the essence of using callback functions in JavaScript. Callback functions are derived from a programming paradigm known as functional programming. At a fundamental level, functional programming specifies the use of functions as arguments.

Luckily there are certain functions provided to iterate on arrays and deliver certain values or transform them into new values. These functions are used in functional programming and are called Higher-Order functions. They are extremely usefull and also improve readability of the code.

The most important functions are:
* forEach
* find
* map
* reduce
* filter

A good ressource for Array functions can be found here:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array

Prefer these functions when looping over arrays. Use polyfills in case a function is not availabe in older browsers.

**Bad:**
```javascript
var fruits = ["Apple", "Banana"];
for (var i = 0; i < fruits.length; i++) {
    console.log(item[i], i);
});
```

**Good:**
```javascript
var fruits = ["Apple", "Banana"];
fruits.forEach(function (item, index) {
    console.log(item, index);
});
```

Or even better when extracting the function so it can be used by another piece of code
```javascript
function logItems(item, index) {
    console.log(item, index);
});

fruits.forEach(logItems);
```

Use filter function for example in order to get filtered results based on a certain value:
```javascript
var allUser = [{
        name: "John",
        blocked: true
    }, {
        name: "Paul",
        blocked: false
    }, {
        name: "Ringo",
        blocked: true
    }];

// Give me all user that are blocked
var blockedUser = allUser.filter(function (user) {
    return user.blocked;
});

// returns: [{ "name": "John", "blocked": true }, { "name": "Ringo", "blocked": true }]
```


### Associative Arrays
Never use Array as a map/hash/associative array.

Associative Arrays are not allowed... or more precisely it's not allowed to use non number indexes for arrays. If you need a map/hash use Object instead of Array in these cases because the features that you want are actually features of Object and not of Array. Array just happens to extend Object (like any other object in JS and therefore you might as well have used Date, RegExp or String).


### Enumerations and constants
JavaScript does not provide something like enumerations or contants but it offers functionality to freeze objects. Based on this, we can build our own enumerations as follows:
```javascript
define("myTypes", Object.freeze({
    NAME: "NAME",
    CIRCLE: "CIRCLE",
    ARC: "ARC"
}));
```

Can be used later as:
```javascript
define([
    "myTypes"
], function (Class, MyTypes) {

    "use strict";

    return {
        update: function (model) {
            if (model.getType() === MyTypes.CIRCLE) {
                    //...
            }
        }
    };
});
```
As APIs grow, enum values may be added, removed or changed. Using strings as enum values ensures that downstream clients can gracefully handle changes to enum values.

This allows for example in the above case to check wether the model has a type or not. If we would use `0` as value, the check for existence of the model type would be false since `0` evaluates to false.

##### AMD module internal constants
AMD module internal constants can be declared at the top as follows. These constants are actually not immutable but it's recommended to use this approach in order to avoid scattering strings arround and to avoid typo mistakes. Not that these values cannot be accessed from outside the module.
```javascript
define("myModule", [
    "jQuery",
    "marionette"
], function ($, Marionette) {

    "use strict";

    var CLASS_TOOLBAR_ITEM = "toolbar-item";

    return Marionette.ItemView.extend({

        updateItem: function (element) {
            if (element.hasClass(CLASS_TOOLBAR_ITEM)) {
                //...
            }
        }
    });
});
```

##### AMD module constants accessible from outside
Constants can also be defined within a module which can be accessed from outside and with as well as provides immutability.

To define such constants, do as follows:
```javascript
define("myToolbar", [
    "marionette"
], function (Marionette) {

    "use strict";

    var MyToolbar = Marionette.ItemView.extend({
        //...
    });

    Object.defineProperty(MyToolbar, "TYPE", {
        value: "TOOLBAR"
    });

    return MyToolbar;
});
```
Not that `Object.defineProperty()` by default is not writable and not configurable. Thus, no need to specify further details.



### Multiline string literals
**No, do not do this:**
```javascript
var myString = "A rather long string of English text, an error message \
    actually that just keeps going and going -- an error \
    message to make the Energizer bunny blush (right through \
    those Schwarzenegger shades)! Where was I? Oh yes, \
    you\'ve got an error and all the extraneous whitespace is \
    just gravy.  Have a nice day.";
```

The whitespace at the beginning of each line can't be safely stripped at compile time; whitespace after the slash will result in tricky errors; and while most script engines support this, it is not part of ECMAScript.

Use string concatenation **instead:**
```javascript
var myString = "A rather long string of English text, an error message " +
    "actually that just keeps going and going -- an error " +
    "message to make the Energizer bunny blush (right through " +
    "those Schwarzenegger shades)! Where was I? Oh yes, " +
    "you\'ve got an error and all the extraneous whitespace is " +
    "just gravy.  Have a nice day.";
```


### Conditional expressions
Use `===` and `!==` over `==` and `!=`. In particular, do not use `==` to compare against falsy values.

Conditional expressions are evaluated using coercion with the ToBoolean method and always follow these simple rules:

* *Objects* evaluate to *true*
* *Undefined* evaluates to *false*
* *Null* evaluates to *false*
* *Booleans* evaluate to *the value of the boolean*
* *Numbers* evalute to *false* if *+0, -0, or NaN*, otherwise *true*
* *Strings* evaluate to *false* if an empty string "", otherwise *true*
```javascript
if ([0]) {
    // true
    // An array is an object, objects evaluate to true
}
```
Use shortcuts.

**Bad:**
```javascript
if (name !== "") {
    // ...stuff...
}

if (collection.length > 0) {
    // ...stuff...
}
```
**Good:**
```javascript
if (name) {
    // ...stuff...
}

if (collection.length) {
    // ...stuff...
}
```


### Type detection
JavaScript is a loosely typed or a dynamic language. That means you don't have to declare the type of a variable ahead of time. The type will get determined automatically while the program is being processed.

JavaScript provides the `typeof` operator to check for a certain type. But the operator should be used with care. Douglas Crockford considers `typeof` an awful part of Javascript since it can introduce unwanted side effects.

The typeof operator takes a value and return it&#8217;s type. There are two possible syntaxes:

* Operator: `typeof x`
* Function-like: `typeof(x)`

The operator evaluates the following:
```javascript
typeof undefined                // "undefined"
typeof 0                        // "number"
typeof true                     // "boolean"
typeof "foo"                    // "string"
typeof new String("lalala")     // "object"
typeof {}                       // "object"
typeof null                     // "object"
typeof new Date                 // "object"
typeof function(){}             // "function"
typeof NaN                      // "number"
```

Consider that:
```javascript
var obj = {};

typeof obj      // returns "object"
typeof null     // returns "object"
```

The `typeof` operator should only be used to identify the type not if the value has been set for an object. To check for existence with `typeof` is considered to be an antipattern.

Therefore **don't do** the following:
```javascript
if (typeof x === "undefined") {
    // ...
}
```

or:
```javascript
if (typeof myObject === null) {
    // ...
}
```

To check for existence **use**:
```javascript
var foo;

if (!foo) {
    console.log("foo does not exist");
}
```
or:
```javascript
var foo = "bar";

if (foo) {
    console.log("foo exists");
}
```


### Ternary operators
Allowed but only single line and not nested. Keep the expression wrapped in parentheses for better readability.
```javascript
var value = (this.ambience.scale) ? this.ambience.scale.value : 1;
```


### Shortcut expression
When checking wether a value is set or not and to use a default value in case it's not set, you can use a shortcut expression.
**Bad:**
```javascript
var value;
if (this.rotation) {
    value = this.rotation;
} else {
    value = 90;
}
```

**Good:**
```javascript
var value = this.rotation || 90;
```


### Coercing
Coerce a value to a type via Boolean, Number, String(), Object() (used as functions &#8211; never use those functions as constructors). Rationale: more descriptive.
```
> + "123"           // no
123
> Number("123")     // yes
123

> "" + true         // no
"true"
> String(true)      // yes
"true"
```

**[back to top](#table-of-contents)**


## JavaScript Style Rules


### Intendation
Use space intendation instead of tabs. Intend code by *4 spaces*. Never mix tabs and space intendation.


### Line length
Avoid lines longer than *100* characters. When a statement will not fit on a single line, it may be necessary to break it. Place the break after an operator, ideally after a comma. A break after an operator decreases the likelihood that a copy-paste error will be masked by semicolon insertion.


### Strings
Use double quotes. Do not mix single and double quotes unless you have to.

Although, single quotes are slightly more common (56% Single Quotes vs 44% Double quotes according to http://sideeffect.kr/popularconvention/#javascript) and they make it easier to work with HTML code (which normally has attribute values in double quotes) but on the other hand, several other languages (C, Java, etc.) only have double-quoted strings (meaning that they look more familiar in JavaScript code). Furthermore, with the JSON format, you don&#8217;t have a choice, you have to double-quote strings.


### Parentheses
Put expressions with operators in parentheses. This improves readability, because it is easier to make out the scopes of the operators and it helps when having multiple conditions on multiple lines.
```javascript
if (propertyName === "position" && type === 1) { ... }          // no
if ((propertyName === "position") && (type === 1)) { ... }      // yes

return foo === bar;             // no
return (foo === bar);           // yes
```

Write parens if a constructor has no arguments. Such a constructor invocation looks cleaner with parentheses.<br>
**Bad:**   `var foo = new Foo;`
**Good**    `var foo = new Foo();`

Be careful about operator precedence. Use parens so that two operators don&#8217;t compete with each other &#8211; the result is not always what you might expect:
```
> false && true || true
true
> false && (true || true)
false
> (false && true) || true
true
```


### Braces & Blocks
Use braces always.

Braces should be used around all statements, even single statements, when they are part of a control structure, such as an if or for statement. This makes it easier to add statements without accidentally introducing bugs.

The opening brace should start at the same line as the expression especially for return statements in order to avoid bug due to automatic semicolon insertion.
It improves readability and visually compresses code for using more screen space.

**Bad:**
```javascript
if (test)
    return false;

if (test) return false;

if (test)
{
    return false;
}

function ()
{
    // ...
}

// Returning an object will result in returnung undefined due to semicolon insertion
return
    {
        id: 1,
        name: "foo"
    };
```

**Good:**
```javascript
if (test) {
    return false;
} else if (anotherTest) {
    return true;
} else {
    // ...
}

function () {
    return false;
}

return {
    id: 1,
    name: "foo"
};
```



### Whitespace
Blank lines improve readability by setting off sections of code that are logically related. Do not use more than one empty line since multiple lines break the flow of reading and decrease readability.
* there are no spaces after opening parentheses and before closing parentheses
* there are spaces after commas
* the word `function` is always followed with one space
* separate functions by a single empty line only.

**Good:**
```javascript
var result = foo("a", "b");
var arr = [1, 2, 3];

if (flag) {
    //...
}

// Add empty line between functions to visually separete them
loadModel: function (options) {
    //...
},

clearScene: function (options) {
    //...
}
```

Always use a single whitespace character for variable assignment and avoid manual alignment since it may be destroyed whith autoformatting files, refactoring or re-intendation using various editors.

**Bad:**
```javascript
var name         = this._name;
var isDefined    = this._isDefined;
var isVisible    = this._isVisible;
var behaviorType = this._behaviorType;
```
**Good:**
```javascript
var name = this._name;
var isDefined = this._isDefined;
var isVisible = this._isVisible;
var behaviorType = this._behaviorType;
```


### Commas
Always *trailing commas*, no leading.

**Bad:**
```javascript
var hero = {
    firstName: "Bob"
    , lastName: "Parr"
    , heroName: "Mr. Incredible"
    , superPower: "strength"
};
```
**Good:**
```javascript
var hero = {
    firstName: "Bob",
    lastName: "Parr",
    heroName: "Mr. Incredible",
    superPower: "strength"
};
```

No additional trailing comma. This may cause problems with IE6/7 and IE9 if it's in quirksmode.

**Bad:**
```javascript
var hero = {
    firstName: "Kevin",
    lastName: "Flynn",
};
var heroes = [
    "Batman",
    "Superman",
];
```
**Good:**
```javascript
var hero = {
    firstName: "Kevin",
    lastName: "Flynn"
};
var heroes = ["Batman", "Superman"];
```


### Formatting AMD modules
The AMD module should be formatted as follows in order to improve readability and flexibility when refactoring imports.

For modules without imports:
```javascript
define("myModule", function () {
    return;
});
```

For modules with imports:
```javascript
define([
    "jquery",
    "underscore",
    "marionette",
    "aggregator",
    "eventids",
    "iscroll",
    "hbs!./template"
], function ($, _, Marionette, aggregator, eventids, IScroll, template) {

    "use strict";

    return Marionette.ItemView.extend({
        ...
    });
});
```
When exceeding the max 100 chars per line, break the imports into another line and indent it by 4 spaces. Avoid trailing comma for the last import.



### Comments
Be generous with comments. It is useful to leave information that will be read at a later time by people (possibly yourself) who will need to understand what you have done. The comments should be well-written and clear, just like the code they are annotating. An occasional nugget of humor might be appreciated. Frustrations and resentments will not.

It is important that comments be kept up-to-date. Erroneous comments can make programs even harder to read and understand.

Make comments meaningful. Focus on what is not immediately visible.

Place comments on a new line above the subject of the comment. Put an empty line before the comment.

**Bad:**
```javascript
var active = true;  // is current tab

function getType () {
    console.log("fetching type...");
    // set the type to "default" if not set
    var type = this._type || "default";

    return type;
}
```
**Good:**
```javascript
// is current tab
var active = true;

function getType () {
    console.log("fetching type...");

    // set the type to "default" if not set
    var type = this._type || "default";

    return type;
}
```

Documentaing AMD modules:
When it is required to document the AMD module itself, it should be done preferably at the top of the AMD function.

Avoid unnecessary comments for the dependency since they are self explanatory.

**Bad:**
```javascript
define('myModule',
// dependencies
[
'marionette'
],
/**
* @module MyModule
*
* @requires module:Marionette
*/
function (UWA)
{
    ...
}
```

**Good**
```javascript
define("myModule", [
    "marionette"
], function (Marionette) {

    /**
    * Comment defining the AMD Module
    * ...
    */

    ...
```


Prefixing your comments with `FIXME` or `TODO` helps other developers quickly understand if you're pointing out a problem that needs to be revisited, or if you're suggesting a solution to the problem that needs to be implemented. These are different than regular comments because they are actionable. The actions are `FIXME -- need to figure this out` or `TODO -- need to implement`.

Use `// FIXME:` to annotate problems
```javascript
function Calculator () {
    // FIXME: shouldn't use a global here
    total = 0;

    return this;
}
```

Use `// TODO:` to annotate solutions to problems or open tasks
```javascript
function Calculator () {
    // TODO: total should be configurable
    this.total = 0;

    return this;
}
```

**[back to top](#table-of-contents)**


## jQuery
 - Prefix jQuery object variables with a $.

**Bad:**
```javascript
var sidebar = $(".sidebar");
```
**Good:**
```javascript
var $sidebar = $(".sidebar");
```

- Cache jQuery lookups.

**Bad:**
```javascript
function setSidebar() {
    $(".sidebar").hide();

    // ...stuff...

    $(".sidebar").show();
}
```
Good:
```javascript
function setSidebar() {
    var $sidebar = $(".sidebar");
    $sidebar.hide();

    // ...stuff...

    $sidebar.show();
}
```

**[back to top](#table-of-contents)**


## JSON Style Guide

The following rules are based on https://google.github.io/styleguide/jsoncstyleguide.xml.

For formatting existing JSON objects, you can use http://jsonlint.com, an online JSON validator and formatter.

### Property Name Guidelines
Property names should conform to the following guidelines:
* Property names should be meaningful names with defined semantics.
* Property names must be camel-cased, ascii strings.
* Reserved JavaScript keywords should be avoided
* Array types should have plural property names. All other property names should be singular.

### Double Quotes
If a property requires quotes, double quotes must be used. All property names must be surrounded by double quotes. Property values of type string must be surrounded by double quotes. Other value types (like boolean or number) should not be surrounded by double quotes.

### Formatting
* Put the opening brace of nested objects on the same line as the property name
* Separate the value from the property name with a single whitespace
* indent properties with 4 spaces instead of tabs
* add arrays or nested object at the end of the object description

```javascript
{
    "company": "Google",
    "website": "http://www.google.com/",
    "address": {
        "line1": "111 8th Ave",
        "line2": "4th Floor",
        "state": "NY",
        "city": "New York",
        "zip": "10011"
    }
}
```

Another example:
```javascript
{
    "data": {
        "kind": "album",
        "title": "My Photo Album",
        "description": "An album in the user's account",
        "items": [{
            "kind": "photo",
            "title": "My First Photo"
        }, {
            "kind": "photo",
            "title": "My First Photo"
        }]
    }
}
```

**[back to top](#table-of-contents)**


## CSS Style Guide

### General Coding Principles
* Don't include styles inline in the document, either in a style tag or on the elements. It's harder to track down style rules.
* Elements that occur only once inside a document should use IDs, otherwise, use classes.
* Write selectors that are optimized for speed. Where possible, avoid expensive CSS selectors. For example, avoid the * wildcard selector.


### Naming Conventions for Selectors
It is always preferable to name something, be it an ID or a class, by the nature of what it is rather than by what it looks like. For instance, a class name of `big-blue-text` for a special note on a page is quite meaningless if it has been changed to have a small red text color. Using a more intelligent convention such as `note-text` is better because when the visual style changes it still makes sense.

Separate words in ID and class names by a hyphen.

**Bad:**
```
.demoImage {}
.demo_image {}
```
**Good:**
```
.demo-image {}
```


### Type Selectors
Avoid qualifying ID and class names with type selectors. Unless necessary (for example with helper classes), do not use element names in conjunction with IDs or classes.

Avoiding unnecessary ancestor selectors is useful for performance reasons.

**Not recommended:**
```
ul#example {}
div.error {}
```
**Recommended:**
```
#example {}
.error {}
```

### 0 and Units
Omit unit specification after &#8220;0&#8221; values. Do not use units after 0 values unless they are required.
```
margin: 0;
padding: 0;
```

Do not omit leading 0s for better reading:
```
font-size: 0.8em;
```


### Spaces
Always add a single space after the css attribute key for better readability.

**Bad:**
```
margin:5px;
padding:5px;
```
**Good:**
```
margin: 5px;
padding: 5px;
```

**[back to top](#table-of-contents)**


## HTML Style Guide

### General Markup Guidelines
The following are general guidelines for structuring your HTML markup.

* Use actual `p` elements for paragraph delimiters as opposed to multiple `br` tags
* Items in list form should always be housed in a `ul`, `ol`, or `dl`, never a set of DIVs or Ps
* Use label fields to label each form field, the for attribute should associate itself with the input field, so users can click the labels. `cursor:pointer;` on the label is wise, as well.
* Do not use the size attribute on your input fields. The size attribute is relative to the font-size of the text inside the input. Instead use css width.
* Tables shouldn't be used for page layout
* Avoid inline CSS in your markup, use a CSS class instead if possible
* Separation of Concerns - Separate structure from presentation from behavior. Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum

### Doctype
A proper Doctype which triggers standards mode in your browser should always be used. Quirks mode should always be avoided.

A nice aspect of HTML5 is that it streamlines the amount of code that is required. Meaningless attributes have been dropped, and the DOCTYPE declaration has been simplified significantly. Additionally, there is no need to use CDATA to escape inline JavaScript, formerly a requirement to meet XML strictness in XHTML.

HTML5 Doctype:
```
<!DOCTYPE html>
```


### Formatting & Style
* Indentation by 4 spaces. Don&#8217;t use tabs or mix tabs and spaces for indentation.
* Use a new line for every block, list, or table element, and indent every such child element.
* Use only lowercase for tags
* Remove trailing white spaces. Trailing white spaces are unnecessary and can complicate diffs.
* Use valid HTML where possible.


### Character Encoding
All markup should be delivered as UTF-8, as its the most friendly for internationalization. It should be designated in both the HTTP header and the head of the document.

Setting the character set using `<meta>` tags.
```
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
```
In HTML5, just do:
```
<meta charset="utf-8">
```

### Markup Comments
```
<!-- this is a single line comment -->

<!--
    this is a
    muti-line comment
-->
```

**[back to top](#table-of-contents)**


## License

(The MIT License)

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[back to top](#table-of-contents)**
