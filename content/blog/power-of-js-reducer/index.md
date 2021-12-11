---

id: 355487
title: Power of Js reducer
published_at: 2020-06-14T16:12:45.371Z
tag_list: javascript,ecmascript,functional,reducer

---

  <img src='https://res.cloudinary.com/practicaldev/image/fetch/s--Vb6sb1sP--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/6vgew46nr1szm8zfrshz.jpg' />

_Reducer_ executes a function (provided as argument to reducer) on each element of the array, resulting in single output value.

### Custom Reducer function

```javascript
const reducer = (array, cb, init) => {
  let result = init
  for (let i = 0; i < array.length; i++) result = cb(result, array[i], i, array)

  return result
}
```

---

### 1. Calculating Length of array using reducer

```javascript
const length = array => reducer(array, (total, currEle) => total + 1, 0)

const list = [1, 2, 3]

console.log(length(list)) // 3
```

---

### 2. Implementing map using Reducer

```javascript
const map = (array, cb) =>
  reducer(array, (acc, currEle) => [...acc, cb(currEle)], [])

const double = n => n * 2
const list = [10, 20, 30, 40]

console.log(map(list, double)) //[ 20, 40, 60, 80 ]
```

---

### 3. Implementing filter using Reducer

```javascript
const filter = (array, cb) =>
  reducer(array, (acc, currEle) => (cb(currEle) ? [...acc, currEle] : acc), [])

const isGreaterThanTwo = n => n > 2
const list = [1, 2, 3, 4]

console.log(filter(list, isGreaterThanTwo)) //[ 3, 4 ]
```

---

### 4. Implementing flatMap using reducer

```javascript
const map = (array, cb) =>
  reducer(array, (acc, currEle) => [...acc, cb(currEle)], [])

const flatMap = (array, cb) =>
  reducer(array, (acc, currEle) => [...acc, ...map(currEle, cb)], [])

const double = n => n * 2
const twoDList = [[1], [2]]

console.log(flatMap(twoDList, double)) //[ 2, 4 ]
```

---

### 5. Implementing forEach using reducer

```javascript
const forEach = (array, cb) =>
  reducer(array, (acc, currEle) => cb(currEle), null)

const printDouble = n => console.log(n * 2)
const list = [20, 40, 50]

forEach(list, printDouble)
/* 
output:
40
80
100
*/
```

---

### 6. Implementing reverse using reducer

```javascript
const reverse = (array, cb) =>
  reducer(array, (acc, currEle) => [currEle, ...acc], [])

const list = ["a", "b"]

console.log(reverse(list)) //[ 'b', 'a' ]
```

---

### 7. Implementing every using reducer

```javascript
const every = (array, condition) =>
  reducer(array, (acc, currEle) => acc && !!condition(currEle), true)

const list = [3, 6]
const isDivisibleByThree = e => e % 3 === 0

console.log(every(list, isDivisibleByThree)) // true
```
