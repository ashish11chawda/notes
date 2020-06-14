# Introduction to Object Oriented Programming JavaScript
- [Procedural Programming](#pp)
- [Object Oriented Programming](#oop)

<h2 id="pp">Procedural Programming</h2>

| F() | Data |
| ----------- | ----------- |
| F() | Data |

**This is program made out of different modules**

> leads to spaghetti code

<h2 id="oop">Object Oriented Programming</h2>

**Object 1**
| F() | Data |
| ----------- | ----------- |
**Object 2**
| F() | Data |
| ----------- | ----------- |
**Program is divided into different Objects**
- Each Object has inter-related Data and methods(functions)

> Best Functions are those with no parameters.

### Benefits of OOP

Encapsulation
: Reduce Complexity and increase reusability

Abstraction
: Reduce Complexity and isolate impact of changes

Inheritance
: Eliminate Redundant code

Polymorphism
: Refactor ugly conditional statements

Poly |  | Morphism
-----|--|-------
Many |  | forms

### Object

#### Object Literal Syntax

```javascript
const object = {} ;
```
*Example*
```javascript
const circle = {
    radius: 1,
    coordinate: {
        x: 1,
        y: 1
    },
    draw: function(){
        console.log('will draw something');
    }
}
```
*Using this Object using ( . ) notation*
```javascript
circle.draw();
```
> If a Object has more than one method then the object is said to have "behaviour", just like a person has.

> Object Literal syntax is not suggested to use for a object which has behaviour.

#### Factory Function
```javascript
function createCircle(radius){
    return {
        radius: radius,
        draw: function(){
            console.log('will draw something');
        }
    }
}
```
*In ES6 if key and values are same then the key value pair can be replaced with value only.**the line `radius: radius,` in return statement can be written as `radius,` only(see code below after changes)*

*This `radius,` is the radius parameter in the function declaration*

```javascript
function createCircle(radius){
    return {
        radius,
        draw: function(){
            console.log('will draw something');
        }
    }
}
```