# Node.js Style Guide

This is a guide for writing consistent and aesthetically pleasing node.js code.
It is inspired by what is popular within the community, and flavored with some
personal opinions.

There is a .jshintrc which enforces these rules as closely as possible. You can
either use that and adjust it, or use
[this script](https://gist.github.com/kentcdodds/11293570) to make your own.

This guide was created by [Felix Geisendörfer](http://felixge.de/) and is
licensed under the [CC BY-SA 3.0](http://creativecommons.org/licenses/by-sa/3.0/)
license. You are encouraged to fork this repository and make adjustments
according to your preferences.

![Creative Commons License](http://i.creativecommons.org/l/by-sa/3.0/88x31.png)

## Table of contents

### Formatting
* [4 Spaces for indentation](#4-spaces-for-indentation)
* [Newlines](#newlines)
* [No trailing whitespace](#no-trailing-whitespace)
* [Use Semicolons](#use-semicolons)
* [100 characters per line](#100-characters-per-line)
* [Use single quotes](#use-single-quotes)
* [Opening braces go on the same line](#opening-braces-go-on-the-same-line)
* [Declare one variable per var statement](#declare-one-variable-per-var-statement)

### Naming Conventions
* [Use lowerCamelCase for variables, properties and function names](#use-lowercamelcase-for-variables-properties-and-function-names)
* [Use UpperCamelCase for class names](#use-uppercamelcase-for-class-names)
* [Use UPPERCASE for Constants](#use-uppercase-for-constants)

### Variables
* [Object / Array creation](#object--array-creation)

### Conditionals
* [Use the === operator](#use-the--operator)
* [Use multi-line ternary operator](#use-multi-line-ternary-operator)
* [Use descriptive conditions](#use-descriptive-conditions)

### Functions
* [Write small functions](#write-small-functions)
* [Return early from functions](#return-early-from-functions)
* [Name your closures](#name-your-closures)
* [No nested closures](#no-nested-closures)
* [Method chaining](#method-chaining)

### Comments
* [Use slashes for comments](#use-slashes-for-comments)

### Miscellaneous
* [Object.freeze, Object.preventExtensions, Object.seal, with, eval](#objectfreeze-objectpreventextensions-objectseal-with-eval)
* [Requires At Top](#requires-at-top)
* [Getters and setters](#getters-and-setters)
* [Do not extend built-in prototypes](#do-not-extend-built-in-prototypes)

## Formatting

### 100 characters per line

Limit your lines to 100 characters.

When a statement will not fit nicely on a single line, it may be necessary to break it. It is best to break after a `{` left brace, `[`, `(`, `,`, or before a `.`, `?`, or `:`. If such a break is not feasible, then break after an operator.

### 4 Spaces for indentation
Use 4 spaces for indentation. No tabs.

### Whitespace
No space should separate an unary operator and its operand except when the operator is a word such as `typeof`.

All binary operators should be separated from their operands by a space on each side except '.' and '(' and '['.

No space is allowed around '[', and '(' with respect to the previous rules.

No space is allowed before ')' and ']' unless they are on a separate line;

Every '{' should be preceded by a space.

Every ',' should be followed by a space or a line break.

Each ';' in the control part of a for statement should be followed with a space.

No trailing spaces are allowed at the end of a line.

### Newlines

Use UNIX-style newlines (`\n`). Windows-style newlines (`\r\n`) are forbidden inside any repository.

Use newlines to group logically related pieces of code.

No newlines at the end of a file.

Each ';' at the end of a statement should be followed with a line break.

### Use Semicolons
Put a `;` semicolon at the end of every simple statement.

### Use single quotes

Use single quotes `'`.

*Right:*

```js
var foo = 'bar';
```

### Opening braces go on the same line

Your opening braces go on the same line as the statement.

*Right:*

```js
if(true) {
    console.log('winning');
}
```

*Wrong:*

```js
if(true)
{
    console.log('losing');
}
```

### Declare variables
All variables should be declared before used.

Declare variables close to their usage.

[crockfordconvention]: http://javascript.crockford.com/code.html

### Array and Object Initializers
Single-line array and object initializers are allowed when they fit on a line:
```
var arr = [1, 2, 3];  // No space after [ or before ].
var obj = {a: 1, b: 2, c: 3};  // No space after { or before }.
```
No space before `,` and `:`. There should be a space after `,` and `:` unless they're the last one in a line.

Multiline array initializers and object initializers are indented 4 spaces, with the braces on their own line, just like blocks.
```
// Object initializer.
var inset = {
    top: 10,
    right: 20,
    bottom: 15,
    left: 12
};

// Array initializer.
this.rows_ = [
    '"Slartibartfast" <fjordmaster@magrathea.com>',
    '"Zaphod Beeblebrox" <theprez@universe.gov>',
    '"Ford Prefect" <ford@theguide.com>',
    '"Arthur Dent" <has.no.tea@gmail.com>',
    '"Marvin the Paranoid Android" <marv@googlemail.com>',
    'the.mice@magrathea.com'
];

// Used in a method call.
goog.dom.createDom(goog.dom.TagName.DIV, {
    id: 'foo',
    className: 'some-css-class',
    style: 'display:none'
}, 'Hello, world!');
```
Only quote keys when your interpreter complains:

*Right:*

```js
var b = {
    good: 'code',
    'is generally': 'pretty',
};
```

### else/catch/finally/while(in do...while)
Put else/catch/finally/while(in do...while) on their own line instead of after '}'.
```
    if(condition1) {
        ...
    }
    else if(condition2) {
        ...
    }
    else {
        ...
    }

    try {
        ...
    }
    catch(err) {
        ...
    }
    finally {
        ...
    }

    do {
        ...
    }
    while(condition);
```
### Conditionals
Short conditional statements may be written on one line if this enhances readability. You may use this only when the line is brief and the statement does not use the else clause.
```
if(x == kFoo) return new Foo();
```
In other cases, curly braces are required.
```
if(condition) {
    doSomething();
}
```

### Switch Statements
Switch statements should always have a default case. If the default case should never execute, simply throw/assert.

case and default clauses have the same identication as swtich.
```
    switch(option) {
    case OPT1:
        ...
    case OPT2:        // No space before colon in a switch case.
        ...
    case OPT3: break; // Use a space after a colon if there's code after it.
    default:
        ...
    }
```
### Loops
Short loop statements may be written on one line if this enhances readability. You may use this only when the line is brief. Otherwise, curly braces are always required.

Empty loop bodies should use {} or continue, but not a single semicolon.
```
for(int i = 0; i < kSomeNumber; ++i) {}  // Good - empty body.
while(condition) continue;  // Good - continue indicates no logic.
```
### Function Declarations
There should be one space between the ')' and the '{' that begins the statement body.

No space should be put between the word function and the '(' in an anonymous function definition.

No space should be put between the function name and the '(' in a function definition or call.

There is never a space between the parentheses and the parameters.

The open curly brace is always on the end of the last line of the function declaration, not the start of the next line.

### Function Calls
When possible, all function arguments should be listed on the same line. If doing so would exceed the 100-column limit, the arguments must be line-wrapped in a readable way. To save space, you may wrap as close to 100 as possible, or put each argument on its own line to enhance readability. The indentation may be either four spaces, or aligned to the parenthesis. Put one blank line between the function declaration and the first statement if they share the same indentation. Below are the most common patterns for argument wrapping:
```
// Four-space, wrap at 100.  Works with very long function names, survives
// renaming without reindenting, low on space.
goog.foo.bar.doThingThatIsVeryDifficultToExplain = function(
    veryDescriptiveArgumentNumberOne, veryDescriptiveArgumentTwo,
    tableModelEventHandlerProxy, artichokeDescriptorAdapterIterator) {
    
    // ...
};

// Four-space, one argument per line.  Works with long function names,
// survives renaming, and emphasizes each argument.
goog.foo.bar.doThingThatIsVeryDifficultToExplain = function(
    veryDescriptiveArgumentNumberOne,
    veryDescriptiveArgumentTwo,
    tableModelEventHandlerProxy,
    artichokeDescriptorAdapterIterator) {
    
    // ...
};

// Parenthesis-aligned indentation, wrap at 100.  Visually groups arguments,
// low on space.
function foo(veryDescriptiveArgumentNumberOne, veryDescriptiveArgumentTwo,
             tableModelEventHandlerProxy, artichokeDescriptorAdapterIterator) {
    // ...
}

// Parenthesis-aligned, one argument per line.  Emphasizes each
// individual argument.
function bar(veryDescriptiveArgumentNumberOne,
             veryDescriptiveArgumentTwo,
             tableModelEventHandlerProxy,
             artichokeDescriptorAdapterIterator) {
  // ...
}
```
When the function call is itself indented, you're free to start the 4-space indent relative to the beginning of the original statement or relative to the beginning of the current function call. The following are all acceptable indentation styles.
```
if (veryLongFunctionNameA(
        veryLongArgumentName) ||
    veryLongFunctionNameB(
    veryLongArgumentName)) {
  veryLongFunctionNameC(veryLongFunctionNameD(
      veryLongFunctioNameE(
          veryLongFunctionNameF)));
}
```

### Binary and Ternary Operators
Always put the operator on the preceding line.
```
var x = a ? b : c;  // All on one line if it will fit.

// Indentation +4 is OK.
var y = a ?
    longButSimpleOperandB : longButSimpleOperandC;

// Indenting to the line position of the first operand is also OK.
var z = a ?
        moreComplicatedB :
        moreComplicatedC;
```

## Naming Conventions
In general, use functionNamesLikeThis, variableNamesLikeThis, ClassNamesLikeThis, EnumNamesLikeThis, methodNamesLikeThis, CONSTANT_VALUES_LIKE_THIS, foo.namespaceNamesLikeThis.bar, and filenameslikethis.js. 

### Properties and methods

    Private properties and methods should be named with a precedent underscore.
    Protected properties and methods should be named without a precedent underscore (like public ones).

### Method and function parameter

Optional function arguments start with opt_.

Functions that take a variable number of arguments should have the last argument named var_args. You may not refer to var_args in the code; use the arguments array.

Optional and variable arguments can also be specified in @param annotations. Although either convention is acceptable to the compiler, using both together is preferred.

### Use lowerCamelCase for variables, properties and function names

Variables, properties and function names should use `lowerCamelCase`.  They
should also be descriptive. Single character variables and uncommon
abbreviations should generally be avoided.

*Right:*

```js
var adminUser = db.query('SELECT * FROM users ...');
```

*Wrong:*

```js
var admin_user = db.query('SELECT * FROM users ...');
```

### Use UpperCamelCase for class names

Class names should be capitalized using `UpperCamelCase`.

*Right:*

```js
function BankAccount() {
}
```

*Wrong:*

```js
function bank_Account() {
}
```

### Use UPPERCASE for Constants

Constants should be declared as regular variables or static class properties,
using all uppercase letters.

*Right:*

```js
var SECOND = 1 * 1000;

function File() {
}
File.FULL_PERMISSIONS = 0777;
```

*Wrong:*

```js
const SECOND = 1 * 1000;

function File() {
}
File.fullPermissions = 0777;
```

[const]: https://developer.mozilla.org/en/JavaScript/Reference/Statements/const
### Filenames

Filenames should be all lowercase in order to avoid confusion on case-sensitive platforms. Filenames should end in `.js`, and should contain no punctuation except for `-` or `_` (prefer `-` to `_`).

## Comments
### Use JSDoc
All files, classes, methods and properties should be documented with JSDoc comments with the appropriate tags and types. Textual descriptions for properties, methods, method parameters and method return values should be included unless obvious from the property, method, or parameter name.

Inline comments should be of the // variety.

Complete sentences are recommended but not required. Complete sentences should use appropriate capitalization and punctuation.
### Comment Syntax 
```
/**
 * A JSDoc comment should begin with a slash and 2 asterisks.
 * Inline tags should be enclosed in braces like {@code this}.
 * @desc Block tags should always start on their own line.
 */
```
### JSDoc Indentation

If you have to line break a block tag, you should treat this as breaking a code statement and indent it four spaces.
```
/**
 * Illustrates line wrapping for long param/return descriptions.
 * @param {string} foo This is a param with a description too long to fit in
 *     one line.
 * @return {number} This returns something that has a description too long to
 *     fit in one line.
 */
project.MyClass.prototype.method = function(foo) {
    return 5;
};
```

## Conditionals

### Use the === operator

Programming is not about remembering [stupid rules][comparisonoperators]. Use
the triple equality operator as it will work just as expected.

*Right:*

```js
var a = 0;
if (a !== '') {
  console.log('winning');
}

```

*Wrong:*

```js
var a = 0;
if (a == '') {
  console.log('losing');
}
```

[comparisonoperators]: https://developer.mozilla.org/en/JavaScript/Reference/Operators/Comparison_Operators

### Use descriptive conditions

Any non-trivial conditions should be assigned to a descriptively named variable or function:

*Right:*

```js
var isValidPassword = password.length >= 4 && /^(?=.*\d).{4,}$/.test(password);

if (isValidPassword) {
  console.log('winning');
}
```

*Wrong:*

```js
if (password.length >= 4 && /^(?=.*\d).{4,}$/.test(password)) {
  console.log('losing');
}
```

## Functions

### Write small functions

Keep your functions short. A good function fits on a slide that the people in
the last row of a big room can comfortably read. So don't count on them having
perfect vision and limit yourself to ~15 lines of code per function.

### Return early from functions

To avoid deep nesting of if-statements, always return a function's value as early
as possible.

*Right:*

```js
function isPercentage(val) {
  if (val < 0) {
    return false;
  }

  if (val > 100) {
    return false;
  }

  return true;
}
```

*Wrong:*

```js
function isPercentage(val) {
  if (val >= 0) {
    if (val < 100) {
      return true;
    } else {
      return false;
    }
  } else {
    return false;
  }
}
```

Or for this particular example it may also be fine to shorten things even
further:

```js
function isPercentage(val) {
  var isInRange = (val >= 0 && val <= 100);
  return isInRange;
}
```

### Name your closures

Feel free to give your closures a name. It shows that you care about them, and
will produce better stack traces, heap and cpu profiles.

*Right:*

```js
req.on('end', function onEnd() {
  console.log('winning');
});
```

*Wrong:*

```js
req.on('end', function() {
  console.log('losing');
});
```

### No nested closures

Use closures, but don't nest them. Otherwise your code will become a mess.

*Right:*

```js
setTimeout(function() {
  client.connect(afterConnect);
}, 1000);

function afterConnect() {
  console.log('winning');
}
```

*Wrong:*

```js
setTimeout(function() {
  client.connect(function() {
    console.log('losing');
  });
}, 1000);
```


### Method chaining

One method per line should be used if you want to chain methods.

You should also indent these methods so it's easier to tell they are part of the same chain.

*Right:*

```js
User
  .findOne({ name: 'foo' })
  .populate('bar')
  .exec(function(err, user) {
    return true;
  });
````

*Wrong:*

```js
User
.findOne({ name: 'foo' })
.populate('bar')
.exec(function(err, user) {
  return true;
});

User.findOne({ name: 'foo' })
  .populate('bar')
  .exec(function(err, user) {
    return true;
  });

User.findOne({ name: 'foo' }).populate('bar')
.exec(function(err, user) {
  return true;
});

User.findOne({ name: 'foo' }).populate('bar')
  .exec(function(err, user) {
    return true;
  });
````

## Comments

### Use slashes for comments

Use slashes for both single line and multi line comments. Try to write
comments that explain higher level mechanisms or clarify difficult
segments of your code. Don't use comments to restate trivial things.

*Right:*

```js
// 'ID_SOMETHING=VALUE' -> ['ID_SOMETHING=VALUE', 'SOMETHING', 'VALUE']
var matches = item.match(/ID_([^\n]+)=([^\n]+)/));

// This function has a nasty side effect where a failure to increment a
// redis counter used for statistics will cause an exception. This needs
// to be fixed in a later iteration.
function loadUser(id, cb) {
  // ...
}

var isSessionValid = (session.expires < Date.now());
if (isSessionValid) {
  // ...
}
```

*Wrong:*

```js
// Execute a regex
var matches = item.match(/ID_([^\n]+)=([^\n]+)/);

// Usage: loadUser(5, function() { ... })
function loadUser(id, cb) {
  // ...
}

// Check if the session is valid
var isSessionValid = (session.expires < Date.now());
// If the session is valid
if (isSessionValid) {
  // ...
}
```

## Miscellaneous

### Object.freeze, Object.preventExtensions, Object.seal, with, eval

Crazy shit that you will probably never need. Stay away from it.

### Requires At Top

Always put requires at top of file to clearly illustrate a file's dependencies. Besides giving an overview for others at a quick glance of dependencies and possible memory impact, it allows one to determine if they need a package.json file should they choose to use the file elsewhere.

### Getters and setters

Do not use setters, they cause more problems for people who try to use your
software than they can solve.

Feel free to use getters that are free from [side effects][sideeffect], like
providing a length property for a collection class.

[sideeffect]: http://en.wikipedia.org/wiki/Side_effect_(computer_science)

### Do not extend built-in prototypes

Do not extend the prototype of native JavaScript objects. Your future self will
be forever grateful.

*Right:*

```js
var a = [];
if (!a.length) {
  console.log('winning');
}
```

*Wrong:*

```js
Array.prototype.empty = function() {
  return !this.length;
}

var a = [];
if (a.empty()) {
  console.log('losing');
}
```
### BE CONSISTENT.

If you're editing code, take a few minutes to look at the code around you and determine its style.

[Felix's Node.js Style Guide](https://github.com/felixge/node-style-guide)
[Google Javascript style guide](https://google.github.io/styleguide/javascriptguide.xml)
[Google C++ style guide](http://google.github.io/styleguide/cppguide.html)
[Crockford's Code Conventions for the JavaScript Programming Language](http://javascript.crockford.com/code.html)
