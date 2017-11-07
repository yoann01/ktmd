---
layout: post
title: Refreshing Next Generation JavaScript 
tags: [javascript, ES6, ES7]
categories:
- blog
---


# ES6/ES7 Syntax Refresh 
###### (Dont worry max i'll update this as soon as possible ^^)

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

>If we change from **var** to **let** the console output will stay the     same, but if wer'e using **const** instead, a **TypeError** will be   returned.   
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
