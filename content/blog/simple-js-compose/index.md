---
id: 379320
title: Simple js compose
description: The concept of compose is simple — it combines n functions. It’s a pipe flowing right-to-left, callin...
published_at: 2020-07-02T19:27:43.847Z
tag_list: javascript,functional,compose
---

The concept of `compose` is simple — it combines n functions. It’s a pipe flowing right-to-left, calling each function with the output of the last one.

```javascript
Array.prototype.reduceRight = function (...args) {
  const _this = this
  return _this.reverse().reduce(...args)
}

const compose =
  (...args) =>
  x =>
    args.reduceRight((acc, currFn) => {
      return currFn(acc)
    }, x)

const double = x => x * 2
const inc = x => x + 1

const incAndOct = compose(double, double, double, inc)

incAndOct(2) //24
```

##### Explanation:

we are passing `2` to `incAndOct` function. First it will call `inc` method then the result will be `3` and next it will apply double method on `3` so result is `6` again one more double but this time on `double(3)` i.e `6` result is 12 now final double on `12` it is `24`
