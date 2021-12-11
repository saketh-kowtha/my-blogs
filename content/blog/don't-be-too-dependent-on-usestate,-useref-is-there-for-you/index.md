---
id: 770444
title: Don't be too dependent on useState, useRef is there for you
published_at: 2021-07-24T15:19:27.034Z
tag_list: beginners,react,nextjs,javascript
---

Hello 👋
Hope all are doing good in this pandemic time.

Whenever i am seeing any reactjs code snippets in internet i am noticing the unnecessary usage of `useState`.

In react updating a state is a very expensive in terms of performance. The main reason is whenever the state updates the component will re-render again.

Here is an small example:
![Screenshot 2021-07-24 at 5.36.02 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627128370241/e2G3yi7dV.png)

In the above code i created a counter using `useState` when i am incrementing the counter `App component` is re-rendering again. There if you check the logs `Component initialised` got printed 4 times (1st time when component initialised and 3 times when i clicked on the `+` button). It is re-rendering the `App component` because i am updating the state on click of the `+` button.

Here we need to use state because our intention is to show the `counter` value in the document.

Consider the following code 👇🏻
![Screenshot 2021-07-24 at 5.51.43 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627129308593/sUNjWfevy.png)

Here i am using two state variables one is for value next is to set type of input. Do we really need two state variables 🤔 ?. Actually why don't we try building this component without state ? the reason why i am saying like this is assume if we are building a form has many input fields in that case we need to pass value state to `input component` from `form component` if that's the case entire form component will re-render on every keystroke in any input.

#### Solution

In the second example actually we don't need state. `useRef` is fine. Check the below code 👇🏻

{% codepen https://codepen.io/saketh-kowtha/pen/yLbzRLr %}

in the ☝🏻 snippet we are not using state but still we able to achieve what we want without out re-rendering. Even in form use case instead if passing state from `form` to `input` we can pass ref it will prevent unnecessary re-renders.

So what i would suggest is whenever you are dealing DOM manipulation like changing class name conditionally or changing any attribute of element etc.. then try to use `useRef` instead of `useState`. it will prevent your app from too many re-renders.

Follow me on
Linkedin : https://www.linkedin.com/in/saketh-kowtha/
Twitter : https://twitter.com/sakethkowtha
Github : https://github.com/saketh-kowtha

You can now extend your support by buying me a Coffee.

<a href="https://www.buymeacoffee.com/sakethk" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
