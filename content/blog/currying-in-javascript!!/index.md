---
id: 798486
title: Currying in javascript!!
description: What is currying ? Currying is an advanced technique of working with functions. It is a...
published_at: 2021-08-20T16:47:39.116Z
tag_list: javascript,react,beginners,webdev
---

### What is currying ?

Currying is an advanced technique of working with functions. It is a transformation of functions that translates a function from callable as f(x, y, x) into callable as f(x)(y)(z).

Example :

```javascript
//Normal function
function add(x, y) {
  return x + y
}

add(1, 2) //3

//Curried function
function add(x) {
  return function (y) {
    return x + y
  }
}

add(1)(2) //3
```

### Why currying

With currying we can break function in to pieces and can reuse those pieces.

"Breaking function in to pieces and reusing" does it sounds crazy ? 🤔

Here is an basic example :

```javascript
function add(x) {
  return function (y) {
    return x + y
  }
}

const addTen = add(10)

addTen(5) //15
addTen(90) //100
```

Now lets see simple real world example

```javascript
function logger(type) {
  function createLogRequest(endPoint) {
    return function (data) {
      return fetch(`<DOMAIN>/${endPoint}`, {
        method: "POST",
        body: data,
      })
    }
  }

  const sendLogs = createLogRequest(type)
  const showLogs = console[type] || console.log

  const transformData = data => `${new Date()} : ${JSON.stringify(data)}`

  return function (logData) {
    const data = transformData(logData)
    sendLogs(data)
    showLogs(data)
  }
}

const infoLog = logger("info")
const errorLog = logger("error")
const warningLog = logger("warning")

infoLog("Some Info....") //Calls /info api and shows info with date
errorLog("Some Error....") //Calls /error api and shows error with date
warningLog("Some Warning....") //Calls /waningr api and shows warning with date
```

#### Function memorisation will be easy

```javascript
const add = a => {
  const memo = {}
  return b => {
    return c => {
      const storedResult = memo[`${a}+${b}+${c}`]
      if (storedResult) return storedResult
      console.log("evaluating")
      const result = a + b + c
      memo[`${a}+${b}+${c}`] = result
      return result
    }
  }
}

const addOne = add(1)
const addThree = addOne(2)
addThree(5)
addThree(5)
addThree(6)
```

### Can we convert normal function to curry function 🤔 ?

Yes of-course with the following code we can use function in both curry and normal way.

Here is an example for that

```javascript
function curry(func) {
  function curried(...args) {
    if (args.length >= func.length) {
      return func.apply(this, args)
    } else {
      return function (...args2) {
        return curried.call(this, ...args, ...args2)
      }
    }
  }
  return curried.bind(this)
}

const add = (a, b, c) => a + b + c

const curriedAdd = curry(add)

//curried
curriedAdd(1)(2)(3) //6

//normal
curriedAdd(1, 2, 3) //6

//curried + normal
curriedAdd(1, 2)(3) //6
```

Hope you learned something new and interesting 🤨

Thank you!!!
