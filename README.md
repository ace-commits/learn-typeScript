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
