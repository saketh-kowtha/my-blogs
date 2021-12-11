---
id: 392279
title: Javascript form validator
published_at: 2020-07-11T06:29:51.871Z
tag_list: javascript,form,validator,es6
---

Here we are going to build a form validator class it will expose four methods `forField`, `addRule`, `validate` and `required`.

#### forField

This method will take field name as argument which we want to validate and returns an current object.

#### addRule

This method will take 3 arguments (fieldName, conditionMethod, failureMessage) first argument is optional if we didn't pass fieldName it will add rules to the current field which we set using `forField`.

#### validate

validate method will take JSON as object, key is field name and value is field value. It will validate based on rules returns `true` if all are valid else it will return error message.

#### required

This method will add required rules for current field

Create a file name it `validator.js`

## Creating Validator class

```javascript
class Validator {}
```

we need to add rules object for validator class

```javascript
rules = {}
```

next we need to add `setField` and `setRule` methods to `Validator` class

```javascript
  setFeild(name) {
    this.feild = name;
    return this;
  }

  setRule(...args) {
    if (this.rules[this.feild])
      this.rules[this.feild].push({ rule: args[0], errMsg: args[1] });
    else this.rules[this.feild] = [{ rule: args[0], errMsg: args[1] }];
  }
```

Now Validator class will be like this

```javascript
class Validator {
  rules = {}

  setField(name) {
    this.field = name
    return this
  }

  setRule(...args) {
    if (this.rules[this.field])
      this.rules[this.field].push({ rule: args[0], errMsg: args[1] })
    else this.rules[this.field] = [{ rule: args[0], errMsg: args[1] }]
  }
}
```

## Adding addField method to validator class

```javascript
Validator.prototype.forField = function (field) {
  this.setField(field)
  return this
}
```

we need two helper functions `_addRule` and `clone`

```javascript
const _addRule = (obj, ...args) => {
  if (args.length === 3) {
    obj.setField(args[0])
    args.shift()
  }
  obj.setRule(...args)
  return clone(obj)
}

function clone(obj) {
  return Object.create(
    Object.getPrototypeOf(obj),
    Object.getOwnPropertyDescriptors(obj)
  )
}
```

## Adding addRule method to validator class

```javascript
Validator.prototype.addRule = function (...args) {
  return _addRule(this, ...args)
}
```

## Adding addRule metohod to validator class

```javascript
Validator.prototype.required = function () {
  const isEmpty = e => !!e
  const capitalize = str => str.charAt(0).toUpperCase() + str.slice(1)
  this.setRule(isEmpty, capitalize(this.field) + " is required")
  return this
}
```

## Adding validate method to validator class

```javascript
Validator.prototype.validate = function (object) {
  const validationFields = Object.keys(this.rules)
  const errorResponses = {}
  let success = true
  validationFields.forEach(item => {
    const validation = this.rules[item].reduce((acc, e) => {
      if (!e.rule(object[item] || "")) {
        success = false
        acc.push(e.errMsg)
      }
      return acc
    }, [])

    if (validation.length > 0) errorResponses[item] = validation
  })

  return {
    success,
    errors: !success ? { ...errorResponses } : {},
  }
}
```

Finally your `validator.js` file will be like this

```javascript
class Validator {
  rules = {}

  setField(name) {
    this.field = name
    return this
  }

  setRule(...args) {
    if (this.rules[this.field])
      this.rules[this.field].push({ rule: args[0], errMsg: args[1] })
    else this.rules[this.field] = [{ rule: args[0], errMsg: args[1] }]
  }
}

Validator.prototype.forField = function (field) {
  this.setField(field)
  return this
}

const _addRule = (obj, ...args) => {
  if (args.length === 3) {
    obj.setField(args[0])
    args.shift()
  }
  obj.setRule(...args)
  return clone(obj)
}

function clone(obj) {
  return Object.create(
    Object.getPrototypeOf(obj),
    Object.getOwnPropertyDescriptors(obj)
  )
}

Validator.prototype.addRule = function (...args) {
  return _addRule(this, ...args)
}

Validator.prototype.required = function () {
  const isEmpty = e => !!e
  const capitalize = str => str.charAt(0).toUpperCase() + str.slice(1)
  this.setRule(isEmpty, capitalize(this.field) + " is required")
  return this
}

Validator.prototype.validate = function (object) {
  const validationFields = Object.keys(this.rules)
  const errorResponses = {}
  let success = true
  validationFields.forEach(item => {
    const validation = this.rules[item].reduce((acc, e) => {
      if (!e.rule(object[item] || "")) {
        success = false
        acc.push(e.errMsg)
      }
      return acc
    }, [])

    if (validation.length > 0) errorResponses[item] = validation
  })

  return {
    success,
    errors: !success ? { ...errorResponses } : {},
  }
}
```

## Working with Validator class

create a file name it `main.js` and add few validation functions

```javascript
const isNumber = e => !isNaN(e)
const isStrType = e => typeof e === "string"
const lengthGtFive = e => e.length > 5
const lengthEqTen = e => e.length === 10
```

Now add the following code to run our Validator

```javascript
const formValidator = new Validator()
const nameRules = formValidator
  .forField("name")
  .addRule(lengthGtFive, "Name Should have atleast 6 letters")
  .required()
const phoneNumberRules = formValidator.addRule(
  "mobile",
  isNumber,
  "Mobile number should only have numbers"
)
nameRules.addRule(isStrType, "Name Should be alphabets")
phoneNumberRules.addRule(lengthEqTen, "Mobile number should have 10 numbers")

//Success Case
formValidator.validate({
  name: "PERSON NAME",
  mobile: "1234567890",
})

/*output
{ success: true, errors: {} }
*/

//Negative Case 1
formValidator.validate({
  name: "PERSO",
  mobile: "1234567890",
})

/*output
{
  success: false,
  errors: { name: [ 'Name Should have atleast 6 letters' ] }
}
*/

//Negative Case 2
formValidator.validate({
  name: "PERSON",
  mobile: "jnlfne",
})

/*output
{
  success: false,
  errors: {
    mobile: [
      'Mobile number should only have numbers',
      'Mobile number should have 10 numbers'
    ]
  }
}
*/
```
