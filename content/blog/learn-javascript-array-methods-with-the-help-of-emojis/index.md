---
id: 790743
title: Learn Javascript array methods with the help of emojis
published_at: 2021-08-13T14:37:13.003Z
tag_list: javascript,webdev,beginners
---

```javascript
//Concat
['ππ»ββοΈ', 'ππ»'].concat('π§π»') = [ 'ππ»ββοΈ', 'ππ»', 'π§π»' ]

//Join
['π€΄π»', 'πΈπ»'].join('π') = 'π€΄π»ππΈπ»'

//Slice
['π­', 'πΆ', 'π'].slice(2)= [ 'π' ]

//Index of
['0οΈβ£', '1οΈβ£', '2οΈβ£', '3οΈβ£'].indexOf('1οΈβ£') = 1

//Includes
['0οΈβ£', '1οΈβ£', '2οΈβ£', '3οΈβ£'].includes('1οΈβ£') = true

//Every
[
{label: '0οΈβ£', type: 'emoji'},
{label: '1οΈβ£', type: 'emoji'},
{label: '2οΈβ£', type: 'emoji'},
{label: '3οΈβ£', type: 'emoji'}
].every(item => item.type === 'emoji') = true

//Some
[0, '1οΈβ£', '2οΈβ£', '3οΈβ£'].some(item => typeof item === 'number') = true

//Fill
['π', 'π', 'π'].fill('π€ͺ') = [ 'π€ͺ', 'π€ͺ', 'π€ͺ' ]

// Map
['0οΈβ£', '1οΈβ£', '2οΈβ£', '3οΈβ£'].map((item, index) => item + " -> " + index) = [ '0οΈβ£ -> 0', '1οΈβ£ -> 1', '2οΈβ£ -> 2', '3οΈβ£ -> 3' ]

// Map
['0οΈβ£', '1οΈβ£', '2οΈβ£', '3οΈβ£'].filter((item, index) => index === 1) = [ '1οΈβ£' ]

//Reduce
['0οΈβ£', '1οΈβ£', '2οΈβ£', '3οΈβ£'].reduce((acc, current) => acc + current) = '0οΈβ£1οΈβ£2οΈβ£3οΈβ£'

//Push
['π€¬', 'π‘', 'π', 'π'].push('π') = 5 // it will insert 'π' to list at last

//unshift
['π‘', 'π', 'π', 'π'].unshift('π€¬') = 5 // it will insert 'π€¬' to list at first

//Pop
['π€¬', 'π‘', 'π', 'π', 'π'].pop('π') = 'π' // it will remove 'π' from list

//Shift
['π€¬', 'π‘', 'π', 'π', 'π'].shift() = 'π€¬' // it will remove 'π€¬' from list

//Reverse
['π€¬', 'π‘', 'π', 'π', 'π'].reverse() = [ 'π', 'π', 'π', 'π‘', 'π€¬' ]

```

Thank you!!
Cheers!!

```

```
