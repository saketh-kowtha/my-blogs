---
id: 772296
title: Advantages of useTimeout and useInterval hooks over setTimeout and setInterval ?
description: Hello 👋 , Hope all are doing good in this pandemic time. In this article i am going to explain...
published_at: 2021-07-26T18:10:59.376Z
tag_list: react,nextjs,javascript,beginners
---

Hello 👋 ,

Hope all are doing good in this pandemic time.

In this article i am going to explain what are advantages of `useTimeout` and `useInterval` hooks over `setTimeout` and `setInterval` also i will show how to create those hooks.

### Why do we need useInterval and useTimeout hooks if we have setTimeout and setInterval.

In Javascript once we initialise `setTimeout` or `setInterval` we cannot modify either callback function or delay time. For better understanding i will explain with an example.

Consider we are building an Alert app which will show the given message to user after N seconds once we click on Done button. Here message and seconds are user inputs. You can refer the 👇🏻 image how the UI will look like

![Screenshot 2021-07-26 at 11.00.31 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627320638279/1jf29rRAo.png)

For this requirement we can blindly code like this

```javascript
const Alert = ({}) => {
  const [message, setMessage] = useState("")
  const [delay, setDelay] = useState(0)

  const messageInputHandler = e => {
    setMessage(e.target.value)
  }

  const dalayInputHandler = e => {
    setDelay(e.target.value)
  }

  const showMessageAfterDelay = () => {
    setTimeout(() => {
      alert(message)
    }, delay * 1000)
  }

  return (
    <div>
      Show <input onChange={messageInputHandler} type="text" /> after
      <input onChange={dalayInputHandler} type="number" /> seconds
      <button onClick={showMessageAfterDelay}>Done</button>
    </div>
  )
}
```

So the above code will work without any issue but if we think in a users prospective we cannot give a guarantee that user will not change the message and delay.

How to handle message and delay dynamically 🤔

we are using `setTimeout` so we need to clear it and we need to call `setTimeout` again with an updated values. Luckily we have `useEffect` we can handle using it now we need to modify our code it will look like 👇🏻

```javascript
const Alert = ({}) => {
  const [message, setMessage] = useState("")
  const [delay, setDelay] = useState(0)

  const messageInputHandler = e => {
    setMessage(e.target.value)
  }

  const dalayInputHandler = e => {
    setDelay(e.target.value)
  }

  const showMessageAfterDelay = () => {
    setTimeout(() => {
      alert(message)
    }, delay * 1000)
  }

  useEffect(() => {
    const idx = setTimeout(() => alert(message), delay)

    return () => clearTimeout(idx)
  }, [message, delay])
  return (
    <div>
      Show <input onChange={messageInputHandler} type="text" /> after
      <input onChange={dalayInputHandler} type="number" />
      seconds
      <button onClick={showMessageAfterDelay}>Done</button>
    </div>
  )
}
```

Here `useEffect` will be called automatically if `message` or `delay` values are updated so do we need `Done` button 🤔 really. Initially we used it to trigger the setTimeout now here `useEffect` is taking care of that

After refactoring the code will be like this 👇🏻

```javascript
const Alert = ({}) => {
  const [message, setMessage] = useState("")
  const [delay, setDelay] = useState(0)

  const messageInputHandler = e => {
    setMessage(e.target.value)
  }

  const dalayInputHandler = e => {
    setDelay(e.target.value)
  }

  useEffect(() => {
    const idx = setTimeout(() => alert(message), delay)

    return () => clearTimeout(idx)
  }, [message, delay])
  return (
    <div>
      Show <input onChange={messageInputHandler} type="text" /> after
      <input onChange={dalayInputHandler} type="number" />
      seconds
    </div>
  )
}
```

We are good with the above one. But after few days we got same scenario in other page but this time we need to change function dynamically instead of message. So how can we achieve this 🤔.

### Solution

We can build a hook called `useTimeout` and can pass `callback function` and `delay` as arguments once any argument got updated that hook itself should update `callback function` and `delay`.

Here is the code for `useTimeout` hook

```javascript
const useTimeout = (fn, delay) => {
  const fnRef = useRef(null)

  //When ever function got updated this👇🏻useEffect will update fnRef
  useEffect(() => {
    fnRef.current = fn
  }, [fn])

  //When ever delay got updated this👇🏻useEffect will clear current one and create a new one with updated delay value
  useEffect(() => {
    const idx = setTimeout(fn, delay)

    return () => clearTimeout(idx)
  }, [delay])

  return
}
```

So now the problem solved similarly we can do it for `useInterval` as well it will be like this 👇🏻

```javascript
const useInterval = (fn, delay) => {
  const fnRef = useRef(null)

  //When ever function got updated this👇🏻useEffect will update fnRef
  useEffect(() => {
    fnRef.current = fn
  }, [fn])

  //When ever delay got updated this👇🏻useEffect will clear current one and create a new one with updated delay value
  useEffect(() => {
    const idx = setInterval(fn, delay)

    return () => clearInterval(idx)
  }, [delay])

  return
}
```

Hope you learned something. Please share and react something 🤨 if you liked it

Thank you 🙏🏻

Follow me on
Linkedin : https://www.linkedin.com/in/saketh-kowtha/
Twitter : https://twitter.com/sakethkowtha
Github : https://github.com/saketh-kowtha
