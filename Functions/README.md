# functions
When creating functions in Javascript, running data types in the parameters that is not meant for the function would usually return undefined. We could error handle, but that requires making conditionals to check the data type of the input first before running any code.

## Argument Types
In TypeScript, you can specify the argument’s data type similar to variables.
```ts
function greet(name: string) {
	console.log(`Hello ${name}`)
}
```
Here we specify that `name` needs to be a string. If given anything else, running `tsc` will return the correct error message.

## Optional Parameters
In Javascript, if no arguments are given, the variable used in the code block becomes undefined or a falsey value. In TypeScript, if no arguments are given, it will return an error instead. 
This may be undesirable. To allow optional arguments do:
```ts
function greet(name?: string) {
	console.log(`Hello ${name || 'Anonymous'}!`)
}
```
The `?` before the argument denotes an optional argument. If no arguments are given when running the function, it will return a falsey statement just like Javascript and will return `Anonymous`.

## Default Parameters
When assigning a parameter a default value, TypeScript will infer the data type as the type of its default value.
For example:
```ts
function greet(name = 'Anonymous') {
	console.log(`Hello ${name || 'Anonymous'}!`)
}
```
> The variable `name` is inferred to be a string or undefined.  
Doing this is cleaner than the function above. 

## Return Types
TS can infer the types of values returned by functions. It looks at the types of the values after a function’s return statement.
```ts
function createGreeting(name: string) {
  return `Hello, ${name}!`;
}
 
const myGreeting = createGreeting('Aisle Nevertell');
```
TS infers the type to be string by:
1. The `return` statement is followed by a string.
2. Arguments provided is a type `string`.

### Explicit Return Types
If we want to specify the return type of a function, we can do that by placing a `: string` after the parameters in a function. 
```ts
function createGreeting(name: string): string {
  return `Hello, ${name}!`;
}

const createArrowGreeting = (name?: string): string => {
	if (name) {
        return `Hello, ${name}!`;
    }
}
 
const myGreeting = createGreeting('Aisle Nevertell');
```
If the function returns anything but a string, it will respond with a type error.

### Void Return Types
If a function doesn’t have a return statement, we can assume the type of the returned value is `void`.
```ts
function logGreeting(name:string): void{
  console.log(`Hello, ${name}!`)
}
```
Here the function merely console logs a statement. To prevent errors and make sure the function purely console.logs only, we can set a return of type `void` to error handle.

### Documentation
In TypeScript, we can add documentation comments to describe the functionality of functions.
```ts
  /**
   * Returns the sum of two numbers.
   *
   * @param x - The first input number
   * @param y - The second input number
   * @returns The sum of `x` and `y`
   *
   */
  function getSum(x: number, y: number): number {
    return x + y;
  }
}
```
Most text editors will display documentation comments when hovering over a function.











