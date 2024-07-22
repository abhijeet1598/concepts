# Asynchronous JavaScript

## How JS executes the code?

JavaScript engines consist of two main components: the heap and the function call stack. Additionally, there is a callback queue, a microtask queue, web APIs/Node APIs, and the event loop.

When JavaScript code executes, a global execution context is created in the call stack, and all synchronous code is directly placed in the call stack. When an asynchronous task is encountered, its callback is placed in the callback queue. Promises have their own special queue, known as the microtask or priority queue, which is executed before the callback queue.

The event loop is responsible for transferring functions from the callback or microtask queue to the call stack whenever the call stack is empty. This mechanism allows JavaScript to handle asynchronous tasks efficiently, giving the appearance of a multi-threaded language, despite being single-threaded.

![JavaScript Execution](https://cdn.hashnode.com/res/hashnode/image/upload/v1638793812677/_05hNt2Da.webp?auto=compress,format&format=webp)

## Synchronus And Asynchronous Code

- **Synchronous (Sync)**: Code is executed line by line. Each operation waits for the previous one to complete before executing.
- **Asynchronous (Async)**: Code does not wait for an operation to complete and can move on to execute other operations. This allows for non-blocking behavior.

## Ways to Make the Code Asynchronous

We can use the following methods:

1. **Callbacks**: Passing a function to be executed after another function completes.
2. **Promises**: An object representing the eventual completion or failure of an asynchronous operation.
3. **Async/Await**: Syntactic sugar built on top of promises, making asynchronous code look synchronous.

## Web Browser APIs

- Web Browser APIs are interfaces provided by the browser to interact with different aspects of the web environment, such as:
  - **DOM API**: Manipulate HTML and CSS
  ```javascript
  const one = document.getElementById("one");
  ```
  - **Fetch API**: Perform network requests. ()
  ```javascript
  fetch("https://example.com")
    .then((data) => console.log(data))
    .catch((error) => console.log(error));
  ```
  - **Web Storage API**: Store data locally.
  ```javascript
  localStorage.set("key", 1);
  ```
  - **Geolocation API**: Get geographical position of the device.

## Event Loop?

- The event loop is a mechanism that allows JavaScript to perform non-blocking operations, despite being single-threaded.
- It continuously checks the call stack and the callback queue(or task queue), putting the callback functions from the callback queue to the call stack if the stack is empty.

# Promises in JavaScript

## Disadvantages of using callback in asynchronous operations

- **Callback Hell**: It refers to the situation where callbacks are nested within other callbacks, leading to code that is hard to read and maintain.

- **Inversion of Control**: When a callback function is passed to another function, control over the execution of the callback is inverted, meaning the function receiving the callback decides when and how to execute it.

## Promise

- A promise is an object representing the eventual completion or failure of an asynchronous operation. It provides a cleaner, more manageable way to handle async operations.

## How to Create a New Promise?

```javascript
const promise = new Promise((resolve, reject) => {
  // async operation
  if (success) {
    resolve("Promised Resolved!");
  } else {
    reject("Error!");
  }
});
```

## States of Promise

Promises has three states:

- **Pending:** By default, a promise has a pending state. It means the promise is neither resolved nor rejected yet.

- **Resolved:** It means the operation is successfully completed and the promise has been fulfilled or resolved.

- **Rejected:** It means the operation has failed and the promise is rejected.

## Ways to consume a promise

1. **Using `.then()` and `.catch()`:** Here .then() handles the fulfillment of the promise and .catch() handles the rejection of the promise.

```javascript
const promise = new Promise((resolve, reject) => {
  // async operation
  if (success) {
    resolve("Promised Resolved!");
  } else {
    reject("Error!");
  }
});

promise
  .then((data) =>
    // code to handle the fulfillment
  )
  .catch((error) =>
    // code to handle the rejection
  )
```

2. **Using Async-Await:** Here await keyword makes the code look synchronous and waits for promise to get either resolved or reject then executes the code further.

```javascript
const promise = new Promise((resolve, reject) => {
  // async operation
  if (success) {
    resolve("Promised Resolved!");
  } else {
    reject("Error!");
  }
});

async function getData() {
  try {
    const data = await promise;
    console.log(data);
  } catch (err) {
    console.log(err);
  }
}

getData();
```

**Note:** Async-Await do not implicitly handles error while consuming the promise. Therefore it needs to be wrapped in a try-catch block to prevent unhandled promise rejection error.

## Chain promises using .then

Promise chaining is used when you are perform a series of asynchronous tasks where each subsequent task is dependent on the previous task.\
In this scenario we can chain the promises using .then where each .then return a value to the next .then avoiding callback hell and better code readibility.

```javascript
promise
  .then((value) => {
    // first handler
    return newValue;
  })
  .then((newValue) => {
    // second handler
    return anotherNewValue;
  })
  .then((anotherNewValue) => {
    // third handler
  })
  .catch((error) => console.log(error));
```

## Handle errors in promises

In promises, a catch block is used to handle the error that might have occured during the asynchronous operation.\
If using .then then .catch can be directly chained with .then block and if using async-await the then .catch needs to used as try-catch block.

```javascript
promise
  .then((data) =>
    // code to handle the fulfillment
  )
  .catch((error) =>
    // code to handle the rejection
  )

OR

try {
  // code to handle the fulfillment
} catch (error) {
  // code to handle the rejection
}
```

## .finally() block in a promise chain

A .finally block will always execute regardless of promise getting resolved or rejected.

```javascript
promise
  .then((value) => {
    // first handler
    return newValue;
  })
  .then((newValue) => {
    // second handler
    return anotherNewValue;
  })
  .then((anotherNewValue) => {
    // third handler
  })
  .catch((error) => {
    // error handler
  })
  .finally(() => {
    // final actions
  });
```

## Behaviour of Error inside a .then()

- **When there is a .catch:** The error is caught and handled by the .catch block.
- **When there is no .catch:** The error propagates and may cause unhandled promise rejection.

## .catch() at the end

The .catch() block must be placed at the end to ensure we catch any error that might have occured in any of the preceding .then() block.

## Promisify an asynchronous callbacks based function

Promifying an synchronous callbacks based function is done by returning a promise from the function which is accepting another function as a callback.\
The returned promise can consumed with JavaScript's modern way of handling asynchrnous operations with promises or async-await.

```javascript
function promisifiedSetTimeout(delay) {
  return new Promise((resolve) => {
    setTimeout(resolve, delay);
  });
}

// Usage with promises
promisifiedSetTimeout(1000).then(() => {
  console.log("1 second has passed");
});

// Usage with async/await
async function usingAwait() {
  await promisifiedSetTimeout(1000);
  console.log("1 second has passed");
}

usingAwait();
```

## Promise based functions

1. **Promise.resolve**

   `Promise.resolve` is used to return a promise that is already resolved with a given value.

```javascript
const resolvedPromise = Promise.resolve("Resolved value");

resolvedPromise.then((value) => {
  console.log(value); // Output: Resolved value
});
```

2. **Promise.reject**

   `Promise.reject` is used to return a promise that is already rejected with a given reason.

```javascript
const rejectedPromise = Promise.reject("Rejected reason");

rejectedPromise.catch((reason) => {
  console.log(reason); // Output: Rejected reason
});
```

3. **Promise.all**

   `Promise.all` is used to wait for all promises to be resolved or for any to be rejected. It takes an array of promises and returns a single promise that resolves when all of the promises in the array have resolved, or rejects with the reason of the first promise that rejects.

```javascript
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, "foo");
});

Promise.all([promise1, promise2, promise3])
  .then((values) => {
    console.log(values); // Output: [3, 42, 'foo']
  })
  .catch((error) => {
    console.error(error);
  });
```

4. **Promise.allSettled**

   `Promise.allSettled` waits for all promises to settle (each may resolve or reject). It returns a promise that resolves after all of the given promises have either resolved or rejected, with an array of objects with each object containing status and value (if resolved) or reason (if rejected).

```javascript
const promise1 = Promise.resolve("resolved");
const promise2 = Promise.reject("rejected");

Promise.allSettled([promise1, promise2]).then((results) => {
  results.forEach((result) => console.log(result));
  // Output:
  // { status: 'fulfilled', value: 'resolved' }
  // { status: 'rejected', reason: 'rejected' }
});
```

5. **Promise.any**

   `Promise.any` takes an array of promises and returns a single promise that resolves with the first promise that fulfills. If none of the promises fulfill (if all of the given promises are rejected), it returns a promise that is rejected with an AggregateError.

```javascript
const promise1 = Promise.reject("Error 1");
const promise2 = Promise.resolve("Success");
const promise3 = Promise.reject("Error 3");

Promise.any([promise1, promise2, promise3])
  .then((value) => {
    console.log(value); // Output: Success
  })
  .catch((error) => {
    console.error(error);
  });
```

6. **Promise.race**

   `Promise.race` returns a promise that resolves or rejects as soon as one of the promises in the array resolves or rejects.

```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, "one");
});
const promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, "two");
});

Promise.race([promise1, promise2]).then((value) => {
  console.log(value); // Output: two
});
```
