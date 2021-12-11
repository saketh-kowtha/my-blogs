---
id: 857646
title: Promisify setTimeout
published_at: 2021-10-09T15:44:17.007Z
tag_list: javascript,webdev,programming,node
---

### Code to promisify `setTimeout`

```javascript
const delay = time =>
  new Promise((resolve, reject) => setTimeout(resolve, time))
```

#### Usage

```javascript
delay(2000).then(() => console.log("Hello i will get logged after 2 second(s)"))
```
