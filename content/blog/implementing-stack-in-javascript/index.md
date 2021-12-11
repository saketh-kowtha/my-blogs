---
id: 791345
title: Implementing Stack in javascript
published_at: 2021-08-14T03:44:10.824Z
tag_list: javascript,beginners,webdev,algorithms
---

Hello 👋,

This is an article on implementing stack data structure in javascript

We already know stack is data structure. It has methods like `push`, `pop`, `top`, `size` and `isEmpty`

![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3iyp6zgqunzf751vv7lc.png)

#### push

It will insert the element at first.

#### pop

It will delete and returns the first element.

### top

It will return first element

### size

It will return size of an stack i.e no of elements in stack

### isEmpty

It will return `true` if stack doesn't have any elements otherwise it will return `false`

```javascript
class Stack {
  constructor() {
    this.list = []
  }

  push(ele) {
    this.list.unshift(ele)
  }

  pop() {
    return this.list.shift()
  }

  top() {
    return this.list[0]
  }

  size() {
    return this.list.length
  }

  isEmpty() {
    return this.list.length === 0
  }
}
```

#### Usage

```javascript
const mystack = new Stack()

mystack.isEmpty() // true
mystack.push("a") // returns undefined but it will add element to list
mystack.push("b")
mystack.push("c")
mystack.isEmpty() // false
mystack.top() // c
mystack.pop() // c
mystack.top() // b
mystack.size() // 2
```

Thank you!!
Cheers!!!
