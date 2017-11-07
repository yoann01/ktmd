---
layout: post
title: Refreshing Next Generation JavaScript 
tags: [javascript, ES6, ES7]
categories:
- blog
---

### ES6/ES7 Syntax Refresh (Dont worry max i'll update this as soon as possible ^^)

## let & const

 **ES6** introduce **let** and  **const** keywords are different way to create variable.
 
>- **let** is use to create variable values.
>- **const** is use to create contant values.

**Exemple**
```js
var myName = 'marc';
console.log(myName); 

myName = 'manu';
console.log(myName); 
```
```sh
>>>Marc
>>>Manu
```

If we change from **var** to **let** the console output will stay the     same, but if wer'e using **const** instead, a **TypeError** will be   returned.   
What's happen is that we're trying to reassigned a variable, myName,    that is declared a **constant** to a new value.   

## Arrow Functions

A normal Javascript function look like this

```js
function myFunc(args){
...
}
```
An **arrow function** look like this
```js
const myFunc = (args) => {
...
}
```
**Exemple**

Normal function
```js
function printMyName(name) {
console.log(name); 
}
printMyName('yoann');
```
```sh
>>>yoann
```

Arrow function
```js
const printMyName = (name) => {
console.log(name); 
}
printMyName('yoann');
```
```sh
>>>yoann
```

## Exports & Imports (Modules)

**person.js**

```js
 const person ={  
       name: 'Max'
    }
 export default person
```
***
**utility.js**

```js
 export const clean = () =>{...}
 export const baseData = 10;
```
***

**app.js**

```js
import person from './person.js'
import prs from './person.js'

import { baseData } from './utility.js'
import { clean } from './utility.js'
```

```js
import * as bundled from './utility.js'
```

*bundle.clean, bundle.baseData ...*


## Classes

**Basic class**
```js
class Person{
    name = 'max'    // Property
    call=()=>{...}  // Methods  

```
**Class instance**
```js
const myPerson = new Person()
myPerson.call()
console.log(myPerson.name)
```

**Inheritance**
```js
class Person extends Master
```

**Exemple**

```js
class Human{
  constructor() {
    this.gender = 'male';
  }
  
  printGender(){
   console.log(this.gender);
  }
}

class Person extend Human{ 
  constructor(){
    super();
    this.name = 'max';
  }
  printMyName() {
    console.log(this.name);
  }
}
const person = new Person();
person.printMyName(); 
```

## Classes, properties & methods

**Properties**
> properties are like " variables attached to classes/ objects"

ES6
```js
constructor(){
	this.myProperty = 'value'
}
```
ES7
```js
myProperty = 'value'
```
****
**Methods**
>Methos are like "function attached to classes/ ojects"


ES6
```js
myMethod(){...}
}
```

ES7
```js
myMethod = () => {...}
}
```

**Exemple**

```js
class Human{
  gender = 'male';

  printGender = () => {
   console.log(this.gender);
  }
}

class Person extend Human{ 
    name = 'max';
  
  printMyName = () => {
    console.log(this.name);
  }
}
const person = new Person();
person.printMyName(); 
```

## Spread & Rest Operators (...)

The **spread** operator is used to split up array elements **OR** object properties.      

```js
const newArray = [...oldArray, 1, 2]
const newObject = {...oldObject, newProp:5}
```

The **rest** operator is used to merge a list of function arguments into an array.      

```js
function sortArgs(...args){
  return args.sort()
}

```
**Exemple**

*spread operator with array*
```js
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4, 5, 6]
console.log(newNumbers );
```
```sh
>>> [1, 2, 3, 4, 5, 6]
```
*spread operator with object*
```js
const Person = {
  name = 'Max'
};

const newPerson = {
...Person, 
age: 28
}
console.log(newPerson );
```
*rest operator*

```js
const filter = (...args) => {
  return args.filter(el=> el === 1);
}
console.log(filter(1, 2, 3));
```
```sh
>>> [1]
```

## Destructuring

> Easily **extract** array elements or objec properties  
> and store them in variables.

**Array** destructuring
```js
[a, b] = ['Hello', 'Max']
console.log(a) //hello
console.log(b) //Max
```

**Obect** destructuring
```js
{name} = {name: 'Max', age: 38]
console.log(name) //Max
console.log(age)  //Undefined
```

**Exemple**
*Array destructuring*
```js
const numbers = [1, 2, 3];
[num1, , num2] = numbers;
console.log(num1, num3);
```
```sh
>>> 1
>>> 3
```
