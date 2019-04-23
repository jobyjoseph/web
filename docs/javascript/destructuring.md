---
id: destructuring
title: Destructuring
---

Destructuring syntax was introduced in ES6. It allows us to work more easily with Arrays and Objects.

## Destructuring with Objects

In order to explain destructuring with objects, first we need to have an object to play with.

```javascript
const car = {
  company: "Mercedes",
  model: "GLS",
  year: 2019
};
```

Our next job is to print the `model` and `year` from the `car` object. For that we are going to assign those 2 properties to a new variable.

```javascript
const model = car.model;
const year = car.year;
console.log(model, year); // GLS 2019
```

There is no big rocket science here. But we tried above lines just to understand the easiness which destructuring brings. In the above lines, you can see we have used the constant names same as that of object properties. That is not by accident. Next, we are going to see how the same assignment operation can be done using destructuring.

```javascript
const { model, year } = car;
console.log(model, year); // GLS 2019
```

What destructuring syntax tells JavaScript engine is that "Go and find out the value of `model` and `year` from `car` object and assign it to corresponding variables." Now, did you get why we used variable names same as that of object properties? What will happen if the code was like this:

```javascript
const { mymodel, year } = car;
```

It will be like "Go and find the value of `mymodel` and `year` from `car`". But, since there is no `mymodel` property inside `car`, `mymodel` will have the value as `undefined`.

## Rename Variables

In the previous section, things worked because we used the variable name and object property name same. But what if we want to have a separate variable name? Then we need to use the renaming syntax.

```javascript
const car = {
  company: "Mercedes",
  model: "GLS",
  year: 2019
};

const { model: mymodel, year } = car;
console.log(mymodel, year); // GLS 2019
```

We need to place a colon(:) after the original property name and then give the new variable name.

> Once we give a new variable name, in our case `mymodel`, we cannot then use `model`. A new variable with name `model` will not be created.

## Setting Defaults

Here is our car object.

```javascript
const car = {
  company: "Mercedes",
  model: "GLS",
  year: 2019
};
```

There is no information about the make of car in the object. So if we are requesting for make of the car, it returns `undefined`.

```javascript
const { make } = car;
console.log(make); // undefined
```

We can set a default value in destructuring. We are going to set a default value of `"German"` to `make`.

```javascript
const { make = "German" } = car;
console.log(make); // German
```

So if the value of `make` is `undefined` in `car` object, it will take the default value which is `"German"` or else the value of the property. So that leads to test an interesting scenario. What if there is a property `make` present in `car` and its value is `undefined`. See my intended object below.

```javascript
const car = {
  company: "Mercedes",
  model: "GLS",
  year: 2019,
  make: undefined
};
```

In this case, what will be the output of following code?

```javascript
const { make = "German" } = car;
console.log(make);
```

If your guess is `undefined`, that is wrong. It will print `German`.

### Default Value and Renaming Together

We learned about setting a default value and also about renaming a variable. We can combine both these functionality like below.

```javascript
const { model: mymodel = "No Model" } = car;
```