---
id: 791464
title: Create own react-redux using context api in react
published_at: 2021-08-14T06:01:29.172Z
tag_list: javascript,react,redux,beginners
---

Hello 👋,

In this article we are going to build own `react-redux` with the help of `context` api

#### Why we need redux in react ?

In react we need to share data between components. It will be very difficult with react state with the help of redux we can make it simple.

Here is an example.

```javascript
const Root = () => {
  const [label, setLabel] = useState()
  return (
    <div>
      <p>{label}</p>
      <Parent setLabel={setLabel} />
    </div>
  )
}

const Parent = props => {
  return <Child {...props} />
}

const Child = props => {
  return <Subchild {...props} />
}

const Subchild = ({ children, setLabel }) => {
  return (
    <div>
      <button onClick={() => setLabel("Hello")}>Set Label</button>
      <p>{children}</p>
    </div>
  )
}
```

In the above example app has multiple levels `Root -> Parent -> Child -> Subchild` we are displaying label in `Root` level and we are setting `label` in Subchild level. For this we need to pass `setLabel` callback till Subchild level from root unnecessarily. Parent and Child has `setLabel` function but those components are not doing anything with that. Here it is small example so it is okay think how can we manage these things in large real time app 🤔

### Solution

REDUX

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628916633404/yJvZ_BFFyw.png)

### How redux helps?

Redux will maintain a store (global state) independently. We can access and mutate the redux data directly from the component. For the above problem we will link `Root` and `Subchild` components with redux so those two components will have an access for global store so `Root` component can access the label at the same time `Subchild` component can set the label no need to pass anything through `Parent` and `Child`

#### Let's jump into development part 🚀

First we need to create context for global state

```javascript
const { createContext } = require("react")

const context = createContext()

const { Provider, Consumer } = context
```

We created context successfully now lets create `combineReducers` along with dummy reducers for now

```javascript
const reducer1 = (state, action) => {
  switch (action.type) {
    case "INSERT_X":
      return { ...state, x: action.data }
    case "DELETE_X":
      return { ...state, x: null }
    default:
      return { ...state }
  }
}

const reducer2 = (state, action) => {
  switch (action.type) {
    case "INSERT_Y":
      return { ...state, y: action.data }
    case "DELETE_Y":
      return { ...state, y: null }
    default:
      return { ...state }
  }
}

// zip is util function
const zip = (list1, list2) => {
  var obj = {}
  for (let i = 0; i < list1.length; i++) {
    obj[list1[i]] = list2[i]
  }
  return obj
}

const combineReducers = reducers => {
  return (state, action) => {
    const _reducers = Object.keys(reducers)
    const _state = Object.keys(reducers).map(reducer => {
      return reducers[reducer](state[reducer], action)
    })

    return zip(_reducers, _state)
  }
}
```

Next we need to create `Provider` method to init store in App and `connect` method to consume it on component

```javascript
const StoreProvider = ({ children }) => {
  const rootReducer = combineReducers({ reducer1, reducer2 })

  const [state, dispatch] = useReducer(rootReducer, {})

  return <Provider value={{ state, dispatch }}>{children}</Provider>
}

const connect = (mapStateTopProps, mapDispatchToProps) => {
  return Component => props => {
    return (
      <Consumer>
        {({ state, dispatch }) => {
          const dispatchProps = mapDispatchToProps(dispatch)
          const stateProps = mapStateTopProps(state)
          return <Component {...props} {...stateProps} {...dispatchProps} />
        }}
      </Consumer>
    )
  }
}
```

Hook approach to mutate and access the state

```javascript
const useSelector = fn => {
  const { state } = useContext(context)
  return fn(state)
}

const useDispatch = fn => {
  const { dispatch } = useContext(context)

  return dispatch
}
```

Finally the code will be like this

```javascript
const {
  useContext,
  createContext,
  useReducer,
  useState,
  useEffect,
} = require("react")

const context = createContext()

const { Provider, Consumer } = context

const reducer1 = (state, action) => {
  switch (action.type) {
    case "INSERT_X":
      return { ...state, x: action.data }
    case "DELETE_X":
      return { ...state, x: null }
    default:
      return { ...state }
  }
}

const reducer2 = (state, action) => {
  switch (action.type) {
    case "INSERT_Y":
      return { ...state, y: action.data }
    case "DELETE_Y":
      return { ...state, y: null }
    default:
      return { ...state }
  }
}

const zip = (list1, list2) => {
  var obj = {}
  for (let i = 0; i < list1.length; i++) {
    obj[list1[i]] = list2[i]
  }
  return obj
}

const combineReducers = reducers => {
  return (state, action) => {
    const _reducers = Object.keys(reducers)
    const _state = Object.keys(reducers).map(reducer => {
      return reducers[reducer](state[reducer], action)
    })

    return zip(_reducers, _state)
  }
}

const Store = ({ children }) => {
  const rootReducer = combineReducers({ reducer1, reducer2 })

  const [state, dispatch] = useReducer(rootReducer, {})

  return <Provider value={{ state, dispatch }}>{children}</Provider>
}

export const connect = (mapStateTopProps, mapDispatchToProps) => {
  return Component => props => {
    return (
      <Consumer>
        {({ state, dispatch }) => {
          const dispatchProps = mapDispatchToProps(dispatch)
          const stateProps = mapStateTopProps(state)
          return <Component {...props} {...stateProps} {...dispatchProps} />
        }}
      </Consumer>
    )
  }
}

export const useSelector = fn => {
  const { state } = useContext(context)
  return fn(state)
}

export const useDispatch = fn => {
  const { dispatch } = useContext(context)

  return dispatch
}

export default Store
```

We are done with redux part 👏🏻

To use this in your app wrap your root component with `StoreProvider` and use `connect` in the components where you want to consume the state

Here is sandbox link with example
{% codesandbox custom-redux-vrkxg %}
Thank you!!!!

🚨🚨⚠️⚠️ : Don’t use this code in production. This is just for educational purposes.

You can now extend your support by buying me a Coffee.

<a href="https://www.buymeacoffee.com/sakethk" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
