---
id: 721764
title: About DOM (Document object model) in HTML
published_at: 2021-06-08T17:18:47.741Z
tag_list: html,javascript,css,webdev
---

### What is DOM ?

DOM (Document object model) is the tree structured data representation of the objects that comprise the structure and content of a document on the web page.

### Who will create this DOM ?

Browser's will generate DOM from HTML.

Here is a simple example
![Dom tree example](https://media.geeksforgeeks.org/wp-content/uploads/DOMExample-3-1.png "Dom tree example")

### Why do we need DOM ?

We can't manipulate HTML directly. There is a way to manipulate i.e extracting the entire HTML of the page, modifying it and replacing the entire HTML document. But this is very complicated and expensive w.r.t performance. So using DOM we can manipulate styles, content and attributes quickly with the help of javascript.

We can see DOM object in browser inspector. This is how it look like

![Dom In Browser](https://www.easeout.co/images/uploads/dom-devtools.png "Dom In Browser")

### How to manipulate DOM ?

Using javascript api's we can manipulate DOM object. Some of them are

- createElement
- appendChild
- removeElement
- querySelector
- querySelectorAll
- insertBefore
- addEventListener
- removeEventListener
- removeChild
- replaceChild
- cloneNode
- setAttribute
- getAttribute
- removeAttribute

Here are some DOM manipulation api examples

```javascript
const btn = document.createElement("button")
const onClick = () => alert("clicked")
btn.textContent = "Creating Node"
document.body.appendChild(btn)
btn.addEventListener("click", onClick)
btn.setAttribute("disabled", true)
btn.removeEventListener("click", onClick)
document.body.removeChild(btn)
```

[Try in Codesandbox](https://codesandbox.io/embed/eloquent-shtern-vt623?fontsize=14&hidenavigation=1&theme=dark)

![Hope you enjoyed](https://media.giphy.com/media/KqZW4NMpogrB0UN6VU/giphy.gif)
