# Async/Await
 
Async/await is a syntax for working with promises that many feel is the easiest and most flexible. This is a new syntax supported in browser but has lived through various iterations in node.js and is present in other languages like c#.
 
How async/await requires that you declare a function as an async function and this function will be awaited using the await keyword when you want to invoke the function in question.
 
You’ll create a function that is intended to perform some asynchronous task and when you are ready to receive the results of that asynchronous function you would await that function in your code. Async functions will return a value and you can assign that value to a variable like you would with any other function that returns a value.
 
## Objectives
 
1. Be able to explain what async/await is and when you'd want to use it.
2. How to declare async functions.
3. how to await the results of your async functions.
4. Where you can use async/await
 
## Declaring an async function
 
```javascript
async function ourFirstAsyncFunction() {
    return 'hello, this is our first await function!!!';
}
```
 
now you can resolve your async function in the same way you would resolve a promise.
 
```javascript
ourFirstAsyncFunction().then((value) => {
    console.log(value);
})
```
 
Notice unlike with promises, we have to invoke our async function to use the 'then' method. This is because an async function returns a promise, it is not in itself a promise.
 
## Using await to resolve our async function
 
We wouldn't normally want to invoke our async function to return a promise and then use the 'then' method to resolve our promise. We can do all of this in a cleaner syntax and that syntax is our await syntax. See below how we could have resolved our async function from above using await.
 
```javascript
const result = await ourFirstAsyncFunction();
console.log(result);
```
 
Something to note at this point. If your async function has a delay, say it is waiting for some API to return some results, our code will pause at the line our await statement is executed on.
 
Another note, await can only be used in the context of an async function, you will get an error if you attempt to use await inside of the context of a function that has not been declared using the async keyword. There is an exception where you can use await at the top level of a module, however for the purposes of this unit we will not be considering this scenarios. Be aware you can use await outside of an async function if you are at the root level of a module, this is due to the asynchronous nature of javascript modules, a topic we will cover in unit 2 with node.js.
 
### example of using await with a fetch
 
```javascript
async function printUsers() {
    const endpoint = 'https://jsonplaceholder.typicode.com/users';
    let users = await fetch(endpoint).then(res => res.json());
    console.log(users);
}
 
printUsers();
```
 
notice how we used our await method on our fetch call. There are a number of native javascript methods that have asynchronous versions that will allow you to use an await like we did with fetch. Also notice we are not returning anything from printUsers(), this is why we did not need to use an await when invoking our printUsers function. If we were to also return a value from our await function, we would then want to await the results of printUsers. See the code snippet below for an example.
 
```javascript
async function fetchUsers() {
    const endpoint = 'https://jsonplaceholder.typicode.com/users';
    let users = await fetch(endpoint).then(res => res.json());
    return users;
}
 
const users = await fetchUsers();
console.log(users)
```
 
notice how our fetchUsers function retrieves users and returns them to our new variable users.

## Resources

[Mozilla async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)

[async/await tutorial](https://javascript.info/async-await)
