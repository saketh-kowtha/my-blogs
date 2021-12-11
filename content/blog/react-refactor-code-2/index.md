---

id: 771525
title: React refactor code #2
description: Actual code : const Counter = ({}) =&gt; { const [counter, setCounter] = useState(0) const...
published_at: 2021-07-26T04:59:01.557Z
tag_list: javascript,webdev,beginners,react

---

**Actual code :**

```javascript
const Counter = ({}) => {
  const [counter, setCounter] = useState(0)

  const reset = () => setCounter(0)

  return (
    <div>
      <p>{counter}</p>
      <button onClick={() => setCounter(counter + 1)}>+</button>
      <button onClick={() => setCounter(counter - 1)}>-</button>
      <button onClick={() => reset()}>Reset</button>
    </div>
  )
}
```

**Refactor stage 1 :**
instead of `setCounter(counter + 1)` if we use `increment()` it would be more readable.

```javascript
const Counter = ({}) => {
  const [counter, setCounter] = useState(0)

  const reset = () => setCounter(0)

  const increment = () => setCounter(counter + 1)

  const decrement = () => setCounter(counter - 1)

  return (
    <div>
      <p>{counter}</p>
      <button onClick={() => increment()}>+</button>
      <button onClick={() => decrement()}>-</button>
      <button onClick={() => reset()}>Reset</button>
    </div>
  )
}
```

**Refactor stage 2 :**
No inline functions

```javascript
const Counter = ({}) => {
  const [counter, setCounter] = useState(0)

  const reset = () => setCounter(0)

  const increment = () => setCounter(counter + 1)

  const decrement = () => setCounter(counter - 1)

  return (
    <div>
      <p>{counter}</p>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
      <button onClick={reset}>Reset</button>
    </div>
  )
}
```
