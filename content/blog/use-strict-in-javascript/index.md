---

id: 615963
title: "use strict" in javascript
description: Javascript is crazy language it will allow us to write bad code that we shouldn't do. use strict dir...
published_at: 2021-02-23T18:00:32.504Z
tag_list: javascript,es5,ecmascript6,webdev

---

<img src='https://res.cloudinary.com/practicaldev/image/fetch/s--pBjfs6-z--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ah5yo18lgm31134qyvq9.jpeg' />
Javascript is crazy language it will allow us to write bad code that we shouldn't do.

`use strict` directive introduced in ECMAScript version 5. It is to indicate that the code should be executed in "strict mode".

This directive will tell to interpreter to turn badly written JavaScript into errors for example.

```javascript
x = 200
console.log(x) // 200
```

Here above snippet is a not a valid JS code because we haven't declared `x` variable with `let`, `var` or `const` so with the help of `use strict` we can solve this problem.

```javascript
"use strict"
x = 200
console.log(x) // ReferenceError: x is not defined
```

## Also helps to ?

This forces developers to write cleaner, more organized, and more readable code in the process. In fact, use strict is used by many famous JavaScript libraries such as ReactJS, jQuery, and more.

## What Exactly use strict will do

###### Here are the some main features that strict mode includes

- Forces proper declaration of variables.

```javascript
x = 200
```

- Prevents global variables.
- Blocks assignment to non-writable global variables.

```javascript
NaN = 1
```

- Blocks repeated object property names.

```javascript
const x = { a: 1, b: 2, a: 3 }
```

- Prevents variable/object hoisting.

---

Strict mode is enabled by default for Ecmascript Modules. Projects built with Babel/Typescript doesn't require it.

Here in [MDN Web Docs Page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) one can read more about the exact functionality of `use strict`.

Thanks 🙏 for reading.
Hope you enjoyed it.
