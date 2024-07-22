# JS Basics

## Values

### Primitive Values

The values which are are directly stored in variable. These include strings, number, boolean, null, undefined. When we copy a primitive value, they are passed by value therefore all the copies will have the same memory address.

### Non-primitive Values

The values are stored as a reference in a variable. These includes arrays, objects, and functions. When we copy a non-primitive value, they are passed by reference therefore all the copies will copies will have different reference even though value can be same.

## Utility Methods

### console.log()

The console.log() method is used print the values on the console. It is very useful in debugging code and understanding the code behaviour.

### Variable Declarations in JS

Javascript has 3 types of variable declaration with keywords like let, var, and const. Following the key differences between these 3:

- Variable declared with `var` can be redeclared and reinitialized.
- Variable declared with `let` can not be redeclared but can be reinitialized.
- Variable declared with `const` can not be redeclared and can not be reinitialized.

### Why primitive values are immutable and Non-primitive values are mutable?

Primitive values are stored directly in the variable. This makes them simple and efficient to use. By making them immutable, JavaScript ensures that their value remains constant.\
Non-primitive values are more complex structures that often represent collections of data. Mutability gives the ablitity to manipulate the data with needing to create new instance of the data structure everytime.

### Rules to follow while naming the variables

1. Choose descriptive names which describes the purpose of the variable just by reading the variable name.\
   For example `userName` instead of `un`.

2. Avoid single letter variable names like a, b, etc.

3. Use camelCase for variable names, starting with a lowercase letter and capitalizing the first letter of each subsequent word.\
   For example `isPlaying` instead of `isplaying` or `Isstudent`.

4. Avoid abbreviation which everyone might not understand.\
   For example `firstName` instead of `fName`.

5. Avoid using keywords as variable names.\
   For example `let const`, `const set`.
