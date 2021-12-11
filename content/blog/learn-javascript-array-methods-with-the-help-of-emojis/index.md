---
id: 790743
title: Learn Javascript array methods with the help of emojis
published_at: 2021-08-13T14:37:13.003Z
tag_list: javascript,webdev,beginners
---

```javascript
//Concat
['🏋🏻‍♂️', '🏃🏻'].concat('🧘🏻') = [ '🏋🏻‍♂️', '🏃🏻', '🧘🏻' ]

//Join
['🤴🏻', '👸🏻'].join('💍') = '🤴🏻💍👸🏻'

//Slice
['😭', '😶', '😀'].slice(2)= [ '😀' ]

//Index of
['0️⃣', '1️⃣', '2️⃣', '3️⃣'].indexOf('1️⃣') = 1

//Includes
['0️⃣', '1️⃣', '2️⃣', '3️⃣'].includes('1️⃣') = true

//Every
[
{label: '0️⃣', type: 'emoji'},
{label: '1️⃣', type: 'emoji'},
{label: '2️⃣', type: 'emoji'},
{label: '3️⃣', type: 'emoji'}
].every(item => item.type === 'emoji') = true

//Some
[0, '1️⃣', '2️⃣', '3️⃣'].some(item => typeof item === 'number') = true

//Fill
['😀', '😃', '😄'].fill('🤪') = [ '🤪', '🤪', '🤪' ]

// Map
['0️⃣', '1️⃣', '2️⃣', '3️⃣'].map((item, index) => item + " -> " + index) = [ '0️⃣ -> 0', '1️⃣ -> 1', '2️⃣ -> 2', '3️⃣ -> 3' ]

// Map
['0️⃣', '1️⃣', '2️⃣', '3️⃣'].filter((item, index) => index === 1) = [ '1️⃣' ]

//Reduce
['0️⃣', '1️⃣', '2️⃣', '3️⃣'].reduce((acc, current) => acc + current) = '0️⃣1️⃣2️⃣3️⃣'

//Push
['🤬', '😡', '🙂', '😊'].push('😄') = 5 // it will insert '😄' to list at last

//unshift
['😡', '🙂', '😊', '😄'].unshift('🤬') = 5 // it will insert '🤬' to list at first

//Pop
['🤬', '😡', '🙂', '😊', '😄'].pop('😄') = '😄' // it will remove '😄' from list

//Shift
['🤬', '😡', '🙂', '😊', '😄'].shift() = '🤬' // it will remove '🤬' from list

//Reverse
['🤬', '😡', '🙂', '😊', '😄'].reverse() = [ '😄', '😊', '🙂', '😡', '🤬' ]

```

Thank you!!
Cheers!!

```

```
