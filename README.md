# Fun facts about Javascript
```
 /\_/\  
( o.o ) 
 > ^ <
```
### 00. Javascript can do extension 
An extension is a feature that allows you to add new functionality to an existing class without modifying original class directly. Extensions are a way to extend the behavior and capabilities of types without subclassing. You to add new functionality to an object after the object is created.

```javascript
// class definition
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
}
// creating an instance of Person
let person = new Person('Kenny', 'Lim');

// extending Person type
Person.prototype.fooBar = function() {
  console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
};

// majik -- person has fooBar method
person.fooBar();
```


### 01. Different ways of defining function
  1. A regular function is hoisted to top level by default, even when the code is the last statement of the file, it will be available everywhere.
  2. In constrast when an arrow function is called before there are defined, it will resolve to an error.
  3. Code inside the arrow function is not compiled until it is being called.
     
```javascript
// creating functions

// with arrow function
const fooBar1 = () => { console.log(`fooBar1`);}

// regular function (hoisted)
function fooBar2() { console.log(`fooBar2`);}
```


### 02. Dot notation and Bracket notation can access/mutate property the same way
You can access/mutate properties in object using both dot notation and bracket notation. Bracket notation is more flexible and allow key to be known at runtime. While dot notation is known before time, more direct and should have slight performance advantage.

```javascript
let person = new Object();

// mutating with dot notation
person.something = 'foo';

// accessing with bracket notation
console.log(person['something']);
```


### 03. Javascript call(...) function reverse the order of calling method
Using Javascript call, we can call a method with function.call(obj, ...) instead of obj.function(...). Various scenarios such as method borrowing & making inheritance possible in Javascript.

```javascript
function greet() {
  console.log(`Hello, ${this.firstName} ${this.lastName}`);
}

const person = { firstName: 'Kenny', lastName: 'Lim' };
// instead of object.method, we are doing method(obj, ...)
greet.call(person);
```


### 04. Javascript call and apply are similar except ...
The apply method is similar to the call method, except that call takes arguments individually, whereas apply takes them as an array. It's useful when you want to invoke a function with a specific context and a variable number of arguments provided in an array-like structure. Making it more dynamic and decide at runtime.

```javascript
function greet(foo) {
  console.log(`${foo}, ${this.firstName} ${this.lastName}`);
}

const person = { firstName: 'Kenny', lastName: 'Lim' };

// using call
greet.call(person, 'foo');

// using apply
greet.apply(person, ['foo']);

```


### 05. Javascript call and bind are similar except ...
The call and bind function are similar. call will run the function, while bind will create the function reference for you to call at a later time.

```javascript
function greet(foo) {
  console.log(`${foo}, ${this.firstName} ${this.lastName}`);
}

const person = { firstName: 'Kenny', lastName: 'Lim' };

// using call
greet.call(person, 'foo');

// using bind
const func = greet.bind(person, 'foo');
func();
```


### 06. Loose equity (==) vs Strict equity
Loose equity will attempt to convert before doing comparison, while strict equity does not convert.

```javascript
// loose equity check
console.log(42 == '42');  // Outputs: true (type coercion: '42' is coerced to number 42)
// strict equity check
console.log(42 === '42');  // Outputs: false (different types)

```


### 07. Proper class inheritance in Javascript
extends keyword is introduced in ES6.

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }
  ...
}

class Student extends Person {
  constructor(name, occupation) {
    super(name);
    this.occupation = occupation;
  }
}
```

### 08. Object deconstructing
Object destructuring allows you to extract properties from an object and assign them to variables in a more concise and convenient way. The name has to match the property name and only need to do assignment on the properties you are interested.

```javascript
const user = {
  name: 'Kenny',
  address: {
    city: 'Klondike',
    postalCode: '98001'
  }
};

const { address: { city, postalCode } } = user;

console.log(city);  
```

### 09. let/xonst vs var

fast vs slow mode
single message queue
async await
offline manifest
wait for one, wait for all
web worker
