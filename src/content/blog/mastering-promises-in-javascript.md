---
title: 'Mastering Promises in JavaScript'
description: 'How JavaScript promises work, why they beat callbacks, and how to use them without getting tangled up.'
pubDate: '2018-06-14'
heroImage: '/images/javascript.jpg'
category: 'JavaScript'
tags: ['JavaScript', 'Promises', 'Async']
---

The first time I worked with promises I spent half a day confused about what was being promised, by whom, and when. The name didn't help. Once it clicked, callback code I'd written for years started to look like a mistake.

Here's the version I wish I'd read in 2014.

## What a Promise Is

A promise is an object that stands in for a value you don't have yet. Something async is happening. The promise represents how that something turns out.

A promise lives in one of three states:

- Pending, if the work isn't done.
- Fulfilled, if the work finished and produced a value.
- Rejected, if the work failed.

The analogy I use: you ask your friend Ben to pick up a chocolate cake. He says yes. That "yes" is the promise. While he's at the bakery, the promise is pending. If he shows up with the cake, fulfilled. If he forgets, rejected.

```js
const promise = benBuysCake('chocolate')
```

Handling the result looks like this:

```js
benBuysCake('chocolate')
  .then(partyAsPlanned)
  .catch(buyCakeYourself)
```

## Why I Stopped Writing Callbacks

Three async operations in a row, callback style:

```js
chargeCustomer(customer, (err, charge) => {
  if (err) return handleError(err)
  addToDatabase(customer, (err, result) => {
    if (err) return handleError(err)
    sendEmail(customer, (err) => {
      if (err) return handleError(err)
      res.send('Success!')
    })
  })
})
```

The same logic with promises:

```js
chargeCustomer(customer)
  .then(() => addToDatabase(customer))
  .then(() => sendEmail(customer))
  .then(() => res.send('Success!'))
  .catch(handleError)
```

One linear chain. One error handler at the bottom. No pyramid. The promise version doesn't just look nicer. It's easier to extend. Adding a fourth step is one more `.then`. Adding a fourth step to the callback version is another nested block and another `if (err) return`.

## Building One

You write a promise with the `Promise` constructor. The constructor takes a function with two arguments, `resolve` and `reject`. Call one of them when the work is done.

```js
const promise = new Promise((resolve, reject) => {
  // do async work
  if (success) {
    resolve(data)
  } else {
    reject(error)
  }
})
```

The cake example, with a delay so it feels real:

```js
const benBuysCake = (cakeType) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (cakeType === 'chocolate') {
        resolve('chocolate cake!')
      } else {
        reject('No cake')
      }
    }, 1000)
  })
}
```

Using it:

```js
benBuysCake('chocolate')
  .then(cake => console.log(cake))
  .catch(err => console.log(err))
```

## Running Promises in Parallel

If you have async work that doesn't depend on each other, `Promise.all` runs it in parallel and waits for everything to finish.

```js
const fries = getFries()
const burger = getBurger()
const drink = getDrink()

Promise.all([fries, burger, drink])
  .then(([fries, burger, drink]) => {
    console.log(`Burger: ${burger}, Fries: ${fries}, Drink: ${drink}`)
  })
  .catch(console.error)
```

Two things to watch for. First, every promise has to resolve, or the whole thing goes to `.catch`. If any one fails, the others are wasted. Second, the resolved array is in the order you passed the promises in, not the order they finished. The fries might come back first. The destructured `[fries, burger, drink]` still lines up.

When partial failure is acceptable, `Promise.allSettled` is the one you want. It hands back results for everything, success or failure.

## Browser Support

Native everywhere modern. If you're stuck supporting IE11 for some reason, the [es6-promise](https://github.com/stefanpenner/es6-promise) polyfill does the job.

## A Note on Callbacks

Callbacks aren't dead. They're still the right tool for event emitters and low-level APIs where there isn't a single eventual value. Node's event loop is built on them. The DOM is built on them.

But for "do one async thing and tell me how it went," promises are the answer. Once you start using them you'll find async code stops feeling like the part of JavaScript you put up with.
