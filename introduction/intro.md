## Javascript ##
- ***Javascript is a lightweight interpreted (or jus-in-time compiled) programming language with first-class functions. While it is most well-known as the scripting language for Web pages, many non-browser environments also use it, such Node.js, Apache CouchDB and Adobe Acrobat. Javascript is a prototype-based, garbage-collected dynamic language, supporting multiple paradigms such as imperative functional, and obejct oriented.***

## First-class Function
- **A programming language is said to have First-class functions when the functions in the language are treated like any other variable. For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable.**

## Assining a function to a variable

```const foo = () => {
console.log("foobar");
};

foo(); //invoke it using the variable

//output: foobar
```
- **We assigned an Anonymous Function in a Variable, then we used that variable to invoke the function by adding parentheses () at the end.**

- **Calling it without '()' will return the function with it's defintion**


## Prototype-based programming
**Prototype-based programming is a style of object-oriented programming in which classes are not explicitly defined, but rather derived by adding properties and methods to an instance of another class or, less frequently, adding them to an empty object.**

**In simple words: this type of style allows the creation of an object without first defining its class.**


## Garbage collection 
**Garbage collection is a term used in computer programming to describe the process of finding and deleting objects which are no longer being referenced by other objects.**


**In other words, garbage collection is the process of removing any objects which are not being used by any other objects. Often abbreviated "GC". Garbage collection is a fundamental component of the memory management system used by Javascript.**

**Some high-level languages, such as JavaScript, utilize a form of automatic memory management known as garbage collection (GC). The purpose of a garbage collector is to monitor memory allocation and determine when a block of allocated memory is no longer needed and reclaim it. This automatic process is an <bold>approximation</bold> since the general problem of determining whether or not a specific piece of memory is still needed is undecidable.**


## Dynamic typing
**Dynamically-typed languages are those where the interpreter assigns variables a type at runtime based on the variables's value at the time.**