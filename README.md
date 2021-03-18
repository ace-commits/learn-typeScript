# Web Development Guide by Bashar Abu Ein

## TypeScript
### Type Annotation and Type Aliasing
TypeScript is a typed language, where we can specify the type of the variables, function parameters and object properties.
We can specify the type using :Type after the name of the variable, parameter, or property. 

```var age: number = 32; // number variable```

**Type Aliasing** refers to creating a new name for a type (kind of like creating a new type, it is really similar to interfaces). 

```
type SalesAppProps = {
  powerAppsPlayerAPIProvider: {
    getResourceToken: (resource: string) => Promise<string>;
  };
}; 
```
Here, we "create" a new type called SalesAppProps which is an object with a single key. The key is called powerAppsPlayerAPIProvider, which is also an object with a single key called getResoruceToken. getResourceToken is a functoin with resource as a prop and returns a Promise. 

### Interfaces
An interface defines an object type, function type, or an array type. It is used for typechecking. An interface is used with the interface keyword. 

#### Interface as an object type
```
interface KeyPair {
    key: number;
    value: string;
}
let kv1: KeyPair = { key:1, value:"Steve" }; // OK
let kv2: KeyPair = { key:1, val:"Steve" }; // Compiler Error: 'val' doesn't exist in type 'KeyPair'
```
Here, we created an interface which defined the structure of a type called KeyPair. kv1 is declared as a KeyPair type. kv1 worked because it matched the type KeyPair. 


#### Interface as a function type
```
interface KeyValueProcessor
{
    (key: number, value: string): void;
};
```
The interface defines a function type called KeyValueProcessor. A function declared with that type should have a key and a value which are a number and string respectively as **props** and should **return** a void.

#### Interface as an array type

```
interface NumList {
    [index:number]:number
}
```
The interface defines an array type which has numerical indices (0,1,2,3,4,..) and the value at each index is a number. 

## JavaScript

### Syntax

### 1
//If the first argument is true, then ourString becomes Hello World!
```
const ourString = true && 'Hello World!'
console.log(ourString)
```
### 2
We use ```else if``` because it allows you to skip unnecessary checks. For example:
```
if()
else if()
else if()
else if()
```
If the first else if() worked, then it doesn't check the next else ifs. This is more efficient. If we only used if statements, then it will check each if statement. 

### Async/Await
#### Example and Explanation 
```
function makePromise(x) { 
    return new Promise(resolve => {
      setTimeout(() => {
        resolve(x);
      }, 1000);
    });
  }
  
  async function asyncFunc() {
    var x = await makePromise(1); // the function is paused here until the promise is fulfilled
    console.log(x); // logs 1
    return x;
  }
  
  const returnedProm = asyncFunc(); // the async func returns a promise

 returnedProm.then((x) => console.log(x));
  // This promise is fulfilled with the return value from the async func, so this logs 1
 ```
- In this example, asyncFunc() is called. It is asynchronous, therefore, you can use await in it.
- Inside asyncFunc(), makePromise(1) is called with await infront of it. 
- **await** causes **asyncFunc** to pause until the promise is settled.
- Inside makePromise(x), the promise resolves after a second. It resolves with the value of x. 
- Therefore, makePromise(1) returns 1, which is why console.log(x) logs 1. 
- **asyncFunc()** returns x:
  - **asyncFunc()** being asynchronous returns a promise. Since the returned value is **x**, this means that the Promise is resolved with the value of **x**. 
  - When an asynchronous function returns a value, in this example it returns x, then the promise is resolved with that value (which means we can access it using .then())
  - When an asynchronous function throws an exception, the Promise will be rejected with the thrown value/exception
- If you try to console.log(returnedProm), it will print a promise, it will not print a value.  
- **.then()** keyword:
  - .then takes in two arguments (both are optional) and it returns a promise which allows for **chaining**:
   - onFulfilled: this is a Function that is called if the Promise is fulfilled. This function has one argument, the fulfillment value.
   - onRejected: this is a Function that is called if the Promise is rejected. This function has one argument, the rejection reason. If it is not a function, it is internally replaced with a "Thrower" function (it throws an error it received as argument).
   - Example:
     ```
      var p1 = new Promise((resolve, reject) => {
      resolve('Success!');
      // or
      // reject(new Error("Error!"));
      });

      p1.then(value => {
      console.log(value); // Success!
      }, reason => {
      console.error(reason); // Error!
      })
     ```
    - Explanation:
      - We created a new promise called p1. The promise constructor takes in a resolution function and a rejection function. 
      - On resolution, the value passed in the resolution function becomes an argument to the onFullfilled function.
- Becuase .then() has access to the resolved value of a promise, then it will have access to x. We pass x to the onFullfilled function of .then() and print it. 
