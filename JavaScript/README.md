# Introduction to Object Oriented Programming JavaScript

- [Introduction to Object Oriented Programming JavaScript](#introduction-to-object-oriented-programming-javascript)
  - [Procedural Programming](#procedural-programming)
  - [Object Oriented Programming](#object-oriented-programming)
    - [Benefits of OOP](#benefits-of-oop)
    - [Object](#object)
      - [Object Literal Syntax](#object-literal-syntax)
      - [Factory Function](#factory-function)
      - [Constructor Function](#constructor-function)
      - [Function as a Object](#function-as-a-object)
      - [Object properties](#object-properties)
      - [Enumerating Object](#enumerating-object)
      - [Getter and Setter](#getter-and-setter)
    - [Data Types](#data-types)
    - [Inheritance](#inheritance)
    - [Classes](#classes)
      - [Sub classes](#sub-classes)
  - [AJAX](#ajax)
    - [Introduction](#introduction)
    - [XmlHttpRequest (XHR) Object](#xmlhttprequest-xhr-object)

## Procedural Programming

| F() | Data |
| --- | ---- |
| F() | Data |

**This is program made out of different modules**

> leads to spaghetti code

## Object Oriented Programming

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

| Poly | Morphism |
| ---- | -------- |
| Many | forms    |

### Object

#### Object Literal Syntax

```javascript
const object = {};
```

_Example_

```javascript
const circle = {
  radius: 1,
  coordinate: {
    x: 1,
    y: 1,
  },
  draw: function () {
    console.log("will draw something");
  },
};
```

_Using this Object using ( . ) notation_

```javascript
circle.draw();
```

> If a Object has more than one method then the object is said to have "behaviour", just like a person has.

> Object Literal syntax is not suggested to use for a object which has behaviour.

**When we use Object Literal syntax to create a object, internally JavaScript uses it's built-in `Object()` constructor function to create that object**

_This can be checked using `objectName.constructor` it returns the method by which that object was created_

_If we write_

```javascript
let x = {};
```

_Internally it is converted to_

```javascript
let x = new Object();
```

#### Factory Function

```javascript
function createCircle(radius) {
  return {
    radius: radius,
    draw: function () {
      console.log("will draw something");
    },
  };
}
```

_In ES6 if key and values are same then the key value pair can be replaced with value only._

_The line `radius: radius,` in return statement can be written as `radius,` only(see code below after changes)_

_This `radius` is the radius parameter in the function declaration_

```javascript
function createCircle(radius) {
  return {
    radius,
    draw: function () {
      console.log("will draw something");
    },
  };
}
```

_Factory function here returns a object in Object literal syntax so, internally it is created using `Object()` constructor then returned to caller_

_Using Factory function_

```javascript
const circle = createCircle(1);
```

#### Constructor Function

**Name of Constructor function must start with `Capital Letter`**

```javascript
function Circle(radius) {
  this.radius = radius;
  this.draw = function () {
    console.log("this will draw something");
  };
  //return this;
}
```

> Constructor Function returns `this` pointer implicitly so there's no return statement needed in this function.

_Using Constructor Function to instantiate the Object_

```javascript
const another = new Circle(1);
```

> When we use `new` operator 3 things happen:
>
> - An Object is created like `{}`.
> - It will set `this` to point to that Object.
> - It will return that Object from used function, in our case it is `Circle(1)`.

> By default `this` points to global Object which is `window object`.

_If we use it like the following or if you forgot to use `new` operator_

```javascript
const another = Circle(1);
```

_then `this` pointer is not made to point the created Object, because by-default it is pointing `window` object_

> Every Object in JavaScript has a property called `constructor`.

**Prototypes**

_Adding a prototype_

```javascript
Circle.prototype.changeRadius = function (newRadius) {
  this.radius = newRadius;
};
```

> This prototype is not part of Object `Circle` itself but it is inheriting it as a prototype.

#### Function as a Object

> In JavaScript functions are Objects.
>
> - There are various methods and properties which can be applied on a function.
>   Example: call, apply, bind, constructor, etc

_Consider following constructor function_

```javascript
function Circle(radius) {
  this.radius = radius;
  this.draw = function () {
    console.log("this will draw something");
  };
  //return this;
}
```

_If you write `Circle.constructor` in console you'll get `Function()` as output_

_we already know functions are objects in JavaScript and these function object are created using JavaScript built-in `Function()` constructor_

_So, above Circle function can also be created using `Function()` constructor as follows:_

```javascript
const Circle = new Function(
  "radius",
  `
        this.radius = radius;
        this.draw = function(){
            console.log("this will draw something");
        }`
);
```

_You can use it as same as we use constructor function to create objects using `new` operator_

#### Object properties

**Adding a Property**

_consider this circle object which has `radius` property and `draw()` method_

```javascript
function Circle(radius) {
  this.radius = radius;
  this.draw = function () {
    console.log("this will draw something");
  };

  const circle = new Circle(1);
}
```

_Following is a way to add property using dot notation_

```javascript
circle.location = { x: 1 };
```

_following is another way if we don't know property name_

```javascript
const propertyName = "location";
circle[propertyName] = { x: 1 };
```

**Deleting a Property**

_using delete opertator_

```javascript
// using dot operator
delete circle.location;

//using bracket notation
delete circle["location"];
```

#### Enumerating Object

_Use for-in loop_

```javascript
for (let key in circle) {
  if (typeof circle[key] !== "function") {
    console.log(key);
  }
}
//using for in loop we can differentiate between properties and methods
```

_Using `keys` method of `Object()`_

```javascript
Object.keys(circle);
//returns array of all properties of an object
//can't differentiate between property and method
```

_Checking is a object has a certain property_

```javascript
if ("radius" in circle) {
  console.log("present");
}
```

#### Getter and Setter

_Consider following Object_

```javascript
function Circle(radius) {

    this.radius = radius;
    //defaultLocation can't be used with dot notation because its scope is only this function
    let defaultLocation = {
      x: 0,
      y: 0
    }

    this.getDefaultLocation = function(){
      return defaultLocation;
    };

    this.draw = function () {
        console.log("this will draw something");
    };

    Object.defineProperty(this, 'defaultLocation', {
        get: function(){
            return defaultLocation;
        },
        set: function(value){
            if(!value.x || !value.y){
                throw new Error('Invalid Location');
            }
            defaultLocation = value;
        }
    });
}

const circle = new Circle(10);
circle.draw();
circle.defaultLocation();
circle.defaultLocation({1,2});
```

### Data Types

| Primitive or Value Types | Reference Types or Objects |
| ------------------------ | -------------------------- |
| Number                   | Object                     |
| String                   | Function                   |
| Boolean                  | Array                      |
| Symbol                   |
| Undefined                |
| Null                     |

> When a object is created and stored in a variable, actually that object is not stored in that variable, instead that object is stored somewhere in memory and its address is stored in variable.

```javascript
let x = { value: 10 };
let y = x;
```

_Here `x` is not storing the object itself but it is storing the address to that Object in memory, I guess that's why Objects are called Reference Types and when we try to copy that object to other entity, it is the reference that is copied not the object itself, so, now both `x` and `y` point to same memory location._

_When we change any of `x` and `y` that change can be immediately reflected at the memory location Object is Present._

```javascript
let x = 10;
```

_Here `x` stores the Number value `10` itself._

> `Primitive Data Types` are copied by their `value`.

> `Objects` are copied by their `Reference`.

### Inheritance

_Shape class inherit circle class although it should be opposite but just consider code snippet for example only_

```javascript
function Shape(type, radius) {
  if (type === "circle") {
    Circle.call(radius);
  }
  this.type = type;
}
```

_Inherit Prototype_

```javascript
Shape.prototype = Object.create(Circle.prototype);
```

_Now any of the Prototype of Circle Object can be used by Shape Object_

_Instantiate Shape Object_

```javascript
const shape1 = new Shape("circle", 1);
//this creates an object of shape circle of radius 1
```

_Now if you check `shape1.prototype.constructor` you'll find out it is still using `Circle()` constructor_

_Use Shape constructor_

```javascript
Shape.prototype.constructor = Shape;
```

### Classes

> It is just Syntactic Sugar, because it uses old ES5 constructor functions underneath.

```javascript
class Book {
  constructor(title, author, year) {
    this.title = title;
    this.author = author;
    this.year = year;
  }

  getSummary() {
    return `${this.title} was written by ${this.author} in ${this.year}`;
  }
  revise(newYear) {
    this.year = newYear;
    this.revised = true;
  }
  static topBookStore() {
    return `My Book Store`;
  }
}

//Instantiate Object
const book1 = new Book("Book 1", "Ashish Chawda", "2020");

//Using static method
book1.topBookStore();
//this line of code will give error as "Not a function"

//So we need class name to use this method as static methods don't need object to be instantiated first
Book.topBookStore();
```

#### Sub classes

```javascript
class Magzine extends Book {
  //extends keyword does the same thing as inheriting the Book class but the easy way
  constructor(title, author, year, month) {
    super(title, author, year); //super() calls parent class' constructor
    this.month = month;
  }
}

//Instantiate Magzine
const mag1 = new Magzine("Mag 1", "John Doe", "2020", "June");
```

## AJAX

### Introduction

- Asynchronous JavaScript and XML
- Set of web technologies
- Send and receive data asynchronously
- Does not interfere with current web page
- JSON has replaced XML for the most part

### XmlHttpRequest (XHR) Object

- API in the form of Object
- Provided by the Browser's JS environment
- Methods transfer data between client/server
- Can be used with other protocols than HTTP
- Can work with data other than XML (JSON, Plain Text)

> **Libraries to make AJAX calls**
>
> - jQuery
> - Axios
> - Superagent
> - Fetch API
> - Prototype
> - Node HTTP
