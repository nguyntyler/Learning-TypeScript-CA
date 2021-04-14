# arrays
To denote a type for arrays, we put a `[]` after the element type.
We can also use `Array<T>` where T stands for the element type.
```ts
let names: string[] = ['Danny', 'Sam']
let names: Array<string> = ['Danny', 'Sam']
```
You can also assign multidimensional arrays. Arrays within arrays.
```ts
let arr: string[][] = [['str1', 'str2'], ['more', 'strings']]
```

# tupes
Similar to the immutability of tuples, we can assign arrays with a fixed sequence of types.
```ts
let ourTuple: [string, number, string, boolean] = ['Is', 7 , 'our favorite number?' , false]; 
```
An array with a fixed type sequence is called a tuple.
They specify:
- The length of the array - A tuple with 3 designated types must have a length of 3.
- The type sequence
As far as JavaScript is concerned, they deal with TypeScript arrays and tuples exactly the same. 

## Inference
TypeScript can infer what kind of variable types you are using.
```ts
let examAnswers= [true, false, false];
```
The above can be read as either `boolean[]` or `[boolean, boolean, boolean]`. Because there is nothing assigned yet, examAnswers is seen as `boolean[]` because it’s less restrictive.  
We can actually do …
```ts
examAnswers[3] = true
```
…and no error will return.
Type inference always returns arrays. To get tuples, we must explicitly denote it with the tuple syntax. A common way of turning a tuple to an array is to use `.concact()` to create a new array with the tuple + another item.

## Rest Parameters
Take this function that combines the parameters given to a string.
```ts
function smush(firstString, ...otherStrings : string[]){
  let output = firstString;
  for(let i = 0; i < otherStrings.length; i++){
    output = output.concat(otherStrings[i]);
  }
  return output;
}
```
By assigning a type annotation to `otherStrings` we can guarantee the type of the arguments given.

## Spread Syntax
Given a very long function, assigning individual type annotations to all the parameters can be a lot.
```ts
function gpsNavigate(startLatitudeDegrees:number, startLatitudeMinutes:number, startNorthOrSouth:string, startLongitudeDegrees: number, startLongitudeMinutes: number, startEastOrWest:string, endLatitudeDegrees:number, endLatitudeMinutes:number , endNorthOrSouth:string, endLongitudeDegrees: number, endLongitudeMinutes: number,  endEastOrWest:string) {
  /* navigation subroutine here */
}
```
We can shorten this by using `tuples`.
- Since the function calls for coordinates from point A to point B, we can break up the parameters in half.
- Point A gets the first half.
- Point B gets the second half.
```ts
let codecademyCoordinates: [number, number, string, number, number, string] = [40, 43.2, 'N', 73, 59.8, 'W'];
let bermudaTCoordinates: [number, number, string, number, number, string] = [25, 0 , 'N' , 71, 0, 'W'];
```
Tuple assignment essentially does the same thing as assigning individual type annotations to the parameters.
Once that is done, we can just use the spread operator inside the arguments portion of the function.
```ts
gpsNavigate(...codecademyCoordinates, ...bermudaTCoordinates);
```

## Full Example
```ts
function performDanceMove(moveName:string, moveReps:number, hasFlair:boolean):void{
  console.log(`I do the ${moveName} ${moveReps} times !`);
  if(hasFlair){
    console.log('I do it with flair!');
  }
}

let danceMoves : [string, number, boolean][] = [
  ['chicken beak', 4, false],
  ['wing flap', 4, false],
  ['tail feather shake', 4, false],
  ['clap', 4, false],
  ['chicken beak', 4, true],
  ['wing flap', 4, true],
  ['tail feather shake', 4, true],
  ['clap', 4, true],
];

for (let i of danceMoves) {
  performDanceMove(...i)
}
```
- `danceMoves` is assigned to be a tuple for error handling.
- We now loop through the array of `danceMoves` and spread each of the sub arrays into the `performDanceMove()` function.









