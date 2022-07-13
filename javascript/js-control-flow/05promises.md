# Promises

A promise is an Javascript object that has a job: go get a particular value. A promise can be in one of three states:

* **Pending:** the promise is in the process of trying to retrieve the value
* **Fulfilled:** the promise has successfully retrieved the value
* **Rejected:** the promise was unable to retrieve the value

### Analogy

Imagine you are stuck at home with a sprained ankle, so you send your friend to the market to buy some pain medication. Your friend is the **promise**. Once your friend has left for the market, the promise is **pending**. If your friend returns from the market with medication, the promise is **fulfilled**. If your friend returns from the market _without_ medication, the promise is **rejected**.

## Creating a Promise

When you create a new promise, you have to tell it what it's job is. Do this buy giving it a callback function.

```javascript
var myPromise = new Promise(myCallback)
```

The promise will pass 2 arguments into the callback: **1.** a function to run if the value is successfully retrieved **2.** a function to run if the value is not successfully retrieved

```javascript
function myCallback(resolve, reject) {
  console.log('pending...');
  if(valueToRetrieve) {
    resolve(valueToRetrieve);
  } else {
    reject('valueToRetrieve is falsey');
  }
}

var valueToRetrieve = "!!!";
var myPromise = new Promise(myCallback);
```

Once a promise is fulfilled, then the promise will represent the value it was sent to retrieve.

```javascript
console.log(myPromise);
```

## Consuming the Promise

Promises are generally _consumed_ by attaching a `.then().catch()`. **.then\(\)**

* triggered by the `resolve()` function
* handles what to do next with the retrieved data

  **.catch\(\)**

* triggered by the `reject()` function
* handles the error

```javascript
function consumePromise(){
    myPromise
        .then(function(retrievedValue){ // will run if resolve() is called
            console.log("fulfilled! retrievedValue is:", retrievedValue);
        }).catch(function(err){ // will run if reject() is called
            console.log("wah wah :( Error:", err);
        })
}

var valueToRetrieve = "!!!";
var myPromise = new Promise(myCallback);
consumePromise();
```

Run this code to see the `.then()` callback run. Change `valueToRetrieve` to a falsey value to see the `.catch()` in action!

## Chaining Promises

You can chain multiple promises together using the `.then()` function. In the callback function of the `.then()`, just return the next promise you want to run:

```javascript
function consumeTwoPromises(){
    myPromise
        .then(function(firstRetrievedValue){
            return new Promise(function(resolve, reject){
                console.log("first retrived value: "+firstRetrievedValue);
                if(firstRetrievedValue){
                    resolve(firstRetrievedValue+"???")
                } else {
                    reject("firstRetrievedValue is falsey");
                }
            })
        })
        .then(function(secondRetrievedValue){ // will run if resolve() is called
            console.log("second retrieved value is:", secondRetrievedValue);
        }).catch(function(err){ // will run if reject() is called
            console.log("wah wah :( Error:", err);
        })
}

var valueToRetrieve = "!!!";
var myPromise = new Promise(myCallback);
consumeTwoPromises();
```

## Asyncronicity

Note that promises are asynchronous. If we add the following `console.log()` statements, they wont necessarily run in the order we'd expect. Try it out!

```javascript
function consumeTwoPromises(){
    console.log("before promises")
    myPromise
        .then(function(firstRetrievedValue){
            return new Promise(function(resolve, reject){
                console.log("first retrived value: "+firstRetrievedValue);
                if(firstRetrievedValue){
                    resolve(firstRetrievedValue+"???")
                } else {
                    reject("firstRetrievedValue is falsey");
                }
            })
        })
        .then(function(secondRetrievedValue){ // will run if resolve() is called
            console.log("second retrieved value is:", secondRetrievedValue);
        }).catch(function(err){ // will run if reject() is called
            console.log("wah wah :( Error:", err);
        })
    console.log("after promises");
}
```

How would you edit this code so that the final `console.log` statement runs _after_ the promises are fulfilled?

## Promise.all()

Promise.all is a method that allows you to resolve multiple promises at the same time. This method will return a collection of values from each promise in the order that they were passed into promise.all as an iterable collection(array). We use promise.all when we have multiple asynchronous requests that need to be resolved before we can proceed with our task. 

A real world example of using promise.all could be we are creating a website that requires information from various different sources and we cannot complete rendering of the webpage until all necessary information has been made available to us. We can create a promise for each of our external requirements and use promise.all to resolve all promises in our prerender steps and then once all of our required resources have been provided, we can begin rendering that content as needed. 

### Promise.all() basic example
```javascript
const promise1 = Promise.resolve('hello');
const promise2 = {
    text: 'this doesn\'t look like a promise?'
};
const promise3 = new Promise((resolve, reject) => {
    const innerValue = 1234;
    if (innerValue % 2 === 0) {
        resolve('This value is even');
    }
    reject('this value isn\'t even');
})

const promiseArray = [promise1, promise2, promise3];
Promise.all(promiseArray).then((values) => {
    console.log(`Values[0]: ${values[0]}`);
    // JSON.stringify can be used to convert an object to a string
    console.log(`Values[1] as a string: ${JSON.stringify(values[1])}`);
    console.log(`Values[1].text: ${values[1].text}`);
    console.log(`Values[2]: ${values[2]}`);
})
```
Note that if you pass a non-promise into your collection of promises that promise will be wrapped in a generic promise, this is something that will only happen when using promise.all, there is no .then or .catch method extensions off of primatives and basic objects in javascript. 

You’d want to use Promise.all instead of changing call backs, as changing callbacks with promises can become extremely tedious and difficult to maintain over time, as well, you will end up writing much more boilerplate code than is needed.

### Promise.all() basic example but with callbacks

This code does the same thing as our code above, however we are not using promise.all and instead using just callbacks. 

```javascript
const promise1 = Promise.resolve('hello');
const promise2 = Promise.resolve({
    text: 'this doesn\'t look like a promise?'
});
const promise3 = new Promise((resolve, reject) => {
    const innerValue = 1234;
    if (innerValue % 2 === 0) {
        resolve('This value is even');
    }
    reject('this value isn\'t even');
})

promise1.then((value1) => {
    console.log(value1);
    promise2.then((value2) => {
        console.log(value2);
        promise3.then((value3) => {
            console.log(value3);
        }).catch((error3) => {
            console.log(error3)
        })
    }).catch((error2) => {
        console.log(error2);
    })
}).catch((error1) => {
    console.log(error1);
})

```

### Catch in Promise.all()

Notice that catch can also be used with promise.all. An important thing to note when using catch and Promise.all is that as soon as any of your promises in your promise collection resolve with a rejection, the promise.all method will immediately jump to the catch statement and no other promises will resolve.

```javascript
const promise1 = Promise.resolve('hello');
const promise2 = {
    text: 'this doesn\'t look like a promise?'
};
const promise3 = new Promise((resolve, reject) => {
    const innerValue = 1234;
    if (innerValue % 2 === 1) {
        resolve('This value is even');
    }
    reject('this value isn\'t even');
})

const promiseArray = [promise1, promise3, promise2];
Promise.all(promiseArray).then((values) => {
    console.log(`Values[0]: ${values[0]}`);
    // JSON.stringify can be used to convert an object to a string
    console.log(`Values[1] as a string: ${JSON.stringify(values[1])}`);
    console.log(`Values[1].text: ${values[1].text}`);
    console.log(`Values[2]: ${values[2]}`);
}).catch((error) => {
    console.log(`an error: ${error}`);
})
```

How would you edit this code so that the final `console.log` statement runs _after_ the promises are fulfilled?

## More Resources

* [Javascript Promises for Dummies](https://scotch.io/tutorials/javascript-promises-for-dummies)
* [cujoJS: Learning Promises](http://know.cujojs.com/tutorials/promises/)
* [Mozilla: Promise.all()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

