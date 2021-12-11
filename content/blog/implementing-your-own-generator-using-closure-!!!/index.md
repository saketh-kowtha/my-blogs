---

id: 355658
title: Implementing your own Generator using closure !!!
published_at: 2020-06-14T17:51:38.401Z
tag_list: javascript,iterator,node,closures

---

  <img src='https://res.cloudinary.com/practicaldev/image/fetch/s--nikfQHcr--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/16h3cwjgboeb9hrx99b8.jpeg' />
  Here is a small program generating x to y numbers using generator in JS later we will implement equivalent function by using closure.

---

### Generating x to y numbers using Generator

---

```javascript
function* genXtoY(x, y) {
  while (x < y) yield x++
  return x++
}

const _iter = genXtoY(1, 5)

_iter.next() //{ value: 1, done: false }
_iter.next() //{ value: 2, done: false }
_iter.next() //{ value: 3, done: false }
_iter.next() //{ value: 4, done: false }
_iter.next() //{ value: 5, done: true }
_iter.next() //{ value: undefined, done: true }
```

---

### Generating x to y numbers using closure

---

```javascript
const genXtoY = (x, y) => {
  const next = () => {
    if (x <= y) return { value: x++, done: x - 1 === y }

    return { value: undefined, done: true }
  }
  return { next }
}

const _iter = genXtoY(1, 5)

_iter.next() //{ value: 1, done: false }
_iter.next() //{ value: 2, done: false }
_iter.next() //{ value: 3, done: false }
_iter.next() //{ value: 4, done: false }
_iter.next() //{ value: 5, done: true }
_iter.next() //{ value: undefined, done: true }
```
