+++
title = "Kodgen & Refureku"
slug = "Kodgen & Refureku"
date = "2020-07-03T00:00:00"
image = ''
description = "C++17 dynamic reflection library"
disableComments = true
draft = false
+++

## Details
- **Technologies / Languages:** C++17, libclang, [toml11](https://github.com/ToruNiina/toml11), Visual Studio 2019, Git, Trello
- **Platform :** Windows / Linux

---

## Introduction

At the beginning, Kodgen and Refureku were a single library, but I thought some of the code could be reused for other purposes, which is the reason why I decided to split the initial codebase into 2 different libraries.

[Kodgen](https://github.com/jsoysouvanh/Kodgen) is a C++17 parsing/code generation library. It is used by Refureku to generate the metadata of each tagged entity in the source code. Entities are tagged using a macro, and it is possible to change this macro very easily thanks to a settings file, or by modifying the parser/generator main directly.

[Refureku](https://github.com/jsoysouvanh/Refureku) is a C++17 dynamic reflection library. It allows to access information about tagged C++ entities like classes or enums.

## Motivation

I wrote this library for a few reasons. First of all, reflection is a programmation concept I like a lot. My past experience on the [Turbo Engine](https://juliensoy.netlify.app/post/turbo-engine/) gave me the motivation to dig further and improve our previous implementation.
Reflection is currently not natively supported by the C++ language, and we won't see anything before C++23 in the standard. On the other hand, C# reflection is extremely powerful and pleasant to use. For that reason, Refureku API is greatly inspired from C# reflection system.

A few C++ reflection libraries already exist, but most of them have flaws I wanted to avoid in my implementation. For example, in some implementations we have to write all reflected information twice: once to declare the entity (let's say a class with several fields and methods), and once again to tell the program to reflect that entity (which means we have to rewrite each field and method of a class/struct). It could look like this:

```cpp
class ExampleClass
{
	private:
		int i;
};

REFLECT_CLASS("ExampleClass", (int) i)
```

Writing things twice is 1. long and 2. error-prone when we modify entities (and god knows that we do!). The good point with that method however is that we can decide what is reflected and what's not. It would be even better if all the codebase could be reflected automatically, but there would be a significant memory footprint (because of third party libraries / STL includes if there are any). That's why it's still good news to be able to choose. Another advantage is that we can attach properties (think of C# properties like System.Serializable, or Unity SerializeField for example) to the reflected entities. It can be very useful to develop a game engine for example.

With Refureku, we just have to tag the entity to reflect with a macro, and we can append attributes as macro parameters to add information on the entity. That way, we write the reflected entity only once, and it is straightforward to edit the code afterwards.

```cpp
#include "Generated/ExampleClass.rfk.h"

class ReflectedClass(ExampleClassAttribute1) ExampleClass
{
	private:
		ReflectedField(ExampleFieldAttribute1, ExampleFieldAttribute2)
		int i;

	ExampleClass_GENERATED
};
```