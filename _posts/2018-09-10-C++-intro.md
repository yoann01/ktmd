---
layout: post
title: C++ intro 
tags: [C++]
categories:
- blog
---

-------
## Functions
- [Introducing function]
- [Retrun Type]
- [Application entry point]
- [Function pointer and std::function](#Function-pointer-and-std::function)
- [Lambda function](#Lambda-function)

-------
## Function pointer and std::function

if you want to store or pass a function. the simplest way of referencing a function 
is a function pointer.

```C
// pointer to variable
int * x = & z;

// pointer to function
int(*x) (int) = &z; // x point to z
```

function pointer syntax is painfull, consider using the std::function type
```C
std::function<int(int)> f = z; // easy
std::function<returntype(arguments type)>
```
-------
## Lambda function

can we store entire functions (rather than pointers to function) in variables?

```C
void foo(){
    int32_t x = 123;

    auto increase_by_x = [&x](int32_t value)
    {
        return x + value;
    };

    int a = 1;
    int b = increase_by_x(a); /// b is 124
}
```
***<sub>note: </sub>*** <br/>
type name = [capturelist](parmeters){body};

* [=] capture everything by value
* [&] capture everything by reference
* [x, &y] capture x by value, y by reference
* [&, z] everythings by reference, excpet z by value

```C
int32_t one = 1;
auto f = [](int32_t x){return x + one}; // error ( variable not specified in the capture list)
```




