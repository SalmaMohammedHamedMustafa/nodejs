# JavaScript Summary

## Variables and Constants

- **`let`** and **`const`** are used to declare variables. `let` allows re-assignment, while `const` does not.
- Example:
    ```javascript
    let firstName = 'salma';
    const NAME = 'salma';
    ```

## Primitive Data Types

- JavaScript has several primitive data types:
    - **String**: `'salma'`, `"cairo"`, `` `Egypt` ``
    - **Number**: `22`, `3.14`
    - **BigInt**: `10n`
    - **Boolean**: `true`, `false`
    - **Undefined**: A variable declared but not assigned a value.
    - **Null**: Explicitly assigned "no value."
    - **Symbol**: A unique and immutable value.
    - **Object**: Collections of key-value pairs, e.g., `{ myName: 'salma', age: 22 }`.

## Dynamically Typed Language

- JavaScript is dynamically typed, meaning variables can change types.
    ```javascript
    let fruit = 'apple';
    fruit = 21;
    ```

## Arrays

- Arrays are objects that hold a list of values.
    ```javascript
    let colors = ['blue', 'red', 'yellow'];
    console.log(colors[0]); // 'blue'
    ```

## Functions

- Functions are blocks of code designed to perform a particular task.
    ```javascript
    function sayHi(name) {
        console.log('hi ' + name);
    }
    
    function add(num1, num2) {
        return num1 + num2;
    }
    ```

## Equality

- **Loose Equality (`==`)**: Converts and compares values.
    ```javascript
    console.log(1 == '1'); // true
    console.log(true == 1); // true
    ```
- **Strict Equality (`===`)**: No type conversion; compares both value and type.
    ```javascript
    console.log(1 === '1'); // false
    console.log(true === 1); // false
    ```

## Ternary Operator

- A concise way to assign a value based on a condition.
    ```javascript
    let age = 16;
    const canDrive = age > 18 ? 'yes' : 'no';
    console.log(canDrive); // 'no'
    ```

## Logical Operators

- **`&&` (AND)**, **`||` (OR)**, **`!` (NOT)**:
    ```javascript
    console.log(true && false); // false
    console.log(true || false); // true
    console.log(!true); // false
    ```

- **Nullish Coalescing (`??`)**: Returns the right-hand side operand when the left-hand side is `null` or `undefined`.
    ```javascript
    let a = null;
    const result = a ?? false;
    console.log(result); // false
    ```

## Operator Precedence

- **`&&`** has higher precedence than **`||`**.
- Example:
    ```javascript
    console.log(false && true || true); // true
    ```

## Conditional Statements

- **`if-else`**: Used for decision making.
    ```javascript
    let hour = 10;
    if (hour >= 6 && hour < 12) {
        console.log('good morning');
    } else if (hour >= 12 && hour < 18) {
        console.log('good afternoon');
    } else {
        console.log('good evening');
    }
    ```

- **`switch`**: For multiple conditional checks.
    ```javascript
    let role = 'guest';
    switch (role) {
        case 'guest':
            console.log('guest user');
            break;
        case 'moderator':
            console.log('moderator user');
            break;
        default:
            console.log('unknown user');
    }
    ```

## Loops

- **`for` loop**: Iterates over arrays or ranges.
    ```javascript
    let numbers = [1, 2, 3, 4, 5];
    for (let i = 0; i < numbers.length; i++) {
        console.log(numbers[i]++);
    }
    ```

- **`while` loop**: Continues until a condition is false.
    ```javascript
    let i = 0;
    while (i < numbers.length) {
        console.log(numbers[i]);
        i++;
    }
    ```

- **`do-while` loop**: Executes at least once before checking the condition.
    ```javascript
    let i = 0;
    do {
        console.log(numbers[i]);
        i++;
    } while (i < numbers.length);
    ```

- **`for-in` loop**: Iterates over the properties of an object.
    ```javascript
    const course = {
        name: 'javascript',
        duration: '2 months',
        price: 100
    };
    for (let key in course) {
        console.log(key, course[key]);
    }
    ```

## Break and Continue

- **`break`**: Exits the loop.
- **`continue`**: Skips to the next iteration.
    ```javascript
    for (let i = 0; i < numbers.length; i++) {
        if (numbers[i] === 3) continue;
        console.log(numbers[i]);
    }
    ```

## Factory and Constructor Functions

- **Factory Function**: Creates objects using a function.
    ```javascript
    function makeDog(name, age) {
        return {
            name,
            age,
            isFriendly: true,
            weight: 20,
            eat: function() {
                this.weight++;
            },
            bark: function() {
                console.log('woof woof');
            }
        };
    }
    ```

- **Constructor Function**: Uses `this` to create objects.
    ```javascript
    function Dog(name, age, weight, isFriendly) {
        this.name = name;
        this.age = age;
        this.weight = weight;
        this.isFriendly = isFriendly;
        this.eat = function() {
            this.weight++;
        };
        this.bark = function() {
            console.log('woof woof');
        };
    }
    const dog1 = new Dog('fluffy', 3, 20, true);
    ```

## Value vs Reference

- **Primitive Types**: Copied by value.
    ```javascript
    let x = 10;
    let y = x;
    x = 20;
    console.log(x); // 20
    console.log(y); // 10
    ```

- **Reference Types**: Copied by reference.
    ```javascript
    let a = { value: 10 };
    let b = a;
    a.value = 20;
    console.log(a.value); // 20
    console.log(b.value); // 20
    ```

## Object Methods

- **`Object.keys()`**: Returns an array of a given object's property names.
    ```javascript
    const keys = Object.keys(person);
    console.log(keys); // ['name', 'height']
    ```

- **`Object.values()`**: Returns an array of a given object's values.
    ```javascript
    const values = Object.values(person);
    console.log(values); // ['salma', 160]
    ```

## Functions as Objects

- Functions are objects in JavaScript, and they have properties like `name`, `length`, and `constructor`.
    ```javascript
    function sayHi() {
        console.log('hi');
    }
    sayHi();
    console.log(sayHi.name); // 'sayHi'
    console.log(sayHi.length); // 0 (number of arguments)
    console.log(sayHi.constructor); // Function constructor
    console.log(sayHi.prototype); // {} (empty object)
    ```

## Object Cloning and Avoiding Reference Issues

In JavaScript, when you assign one object to another, they both reference the same object in memory. Therefore, modifying one will affect the other.

```javascript
let a = { value: 10 };
let b = a;
a.value = 20;
console.log(b); // { value: 20 }
```

### Solution: Using `Object.assign()` Method

To avoid this issue, you can create a copy of the object using the `Object.assign()` method, which creates a shallow copy of the object.

```javascript
let a = { value: 10 };
let b = {};
Object.assign(b, a);
// Alternatively: let b = { ...a }; // Another way to clone an object
a.value = 20;
console.log(b); // { value: 10 }
```

## Garbage Collection in JavaScript

In JavaScript, memory management is handled by the garbage collector, which automatically allocates and deallocates memory, so developers don't need to worry about it.

## Built-in Math Functions

JavaScript provides several built-in functions to handle mathematical operations:

```javascript
console.log(Math.random()); // Random number between 0 and 1
console.log(Math.random() * 10); // Random number between 0 and 10
console.log(Math.random() * 10 + 1); // Random number between 1 and 10
console.log(Math.round(1.9)); // 2
console.log(Math.ceil(1.1)); // 2
console.log(Math.floor(1.9)); // 1
console.log(Math.max(1, 2, 3, 4)); // 4
console.log(Math.min(1, 2, 3, 4)); // 1
```

## Strings in JavaScript

JavaScript has both string primitives and string objects.

```javascript
const message = 'This is my first message'; // String primitive
const another = new String('hi'); // String object

console.log(typeof message); // string
console.log(typeof another); // object
```

### String Methods

JavaScript provides many methods for string manipulation:

```javascript
console.log(message.length); // 24
console.log(message[0]); // T
console.log(message.includes('is')); // true
console.log(message.startsWith('This')); // true
console.log(message.endsWith('message')); // true
console.log(message.indexOf('is')); // 2
console.log(message.replace('first', 'second')); // This is my second message
console.log(message.toUpperCase()); // THIS IS MY FIRST MESSAGE
console.log(message.toLowerCase()); // this is my first message
console.log(message.trim()); // This is my first message
console.log(message.split(' ')); // [ 'This', 'is', 'my', 'first', 'message' ]
```

## Template Literals

Template literals simplify string creation and formatting:

```javascript
let name = 'John';
let greet = 'hi';
let message1 = greet + ' ' + name + ',\n'; // Manual formatting
let message2 = `${greet} ${name},`; // Using template literals
console.log(message1);
console.log(message2);
```

## Date Handling

JavaScript provides a `Date` object for handling dates and times:

```javascript
const now = new Date();
const date1 = new Date('May 11 2018 09:00');
const date2 = new Date(2018, 4, 11, 9); // Month is zero-based
now.setFullYear(2017);
console.log(now.getDate());
console.log(now.getMonth());
console.log(now.getDate());
console.log(now.getFullYear());
console.log(now.getHours());
console.log(now.getMinutes());
console.log(now.getSeconds());
```

## Working with Arrays

### Adding Elements

You can add elements to the beginning, middle, or end of an array:

```javascript
const numbers = [3, 4];
numbers.push(5, 6, 7); // Add to the end
numbers.unshift(0, 1, 2); // Add to the beginning
numbers.splice(2, 0, 'a', 'b'); // Add to the middle
console.log(numbers); // [0, 1, 'a', 'b', 2, 3, 4, 5, 6, 7]
```

### Finding Elements

You can find elements in an array using various methods:

```javascript
const numbers1 = [1, 2, 3, 4, 2];
const index = numbers1.indexOf(2);
const lastIndex = numbers1.lastIndexOf(2);
console.log(index); // 1
console.log(lastIndex); // 4
console.log(numbers1.indexOf(10));  // -1
console.log(numbers1.includes(10)); // false
```

### Working with Objects in Arrays

You can search for objects in an array using `find()`:

```javascript
const courses = [
    { id: 1, name: 'a' },
    { id: 2, name: 'b' }
];
const course = courses.find(course => course.name === 'a');
console.log(course); // { id: 1, name: 'a' }
```

### Arrow Functions

Arrow functions provide a concise syntax for writing functions:

```javascript
// Function declaration
function greet1() {
    console.log('hi');
}
// Function expression
let greet2 = function() {
    console.log('hi');
};
// Arrow function
let greet3 = () => console.log('hi');
// Arrow function with parameters
let greet4 = name => console.log('hi ' + name);
```

### Removing Elements

You can remove elements from the beginning, middle, or end of an array:

```javascript
const numbers2 = [1, 2, 3, 4];
const last = numbers2.pop(); // Remove from the end
const first = numbers2.shift(); // Remove from the beginning
numbers2.splice(1, 1); // Remove from the middle
console.log(numbers2); // [1, 3, 4]
```

### Clearing an Array

There are several ways to clear an array:

```javascript
let numbers3 = [1, 2, 3, 4];
let another1 = numbers3;

// Solution 1
// numbers3 = []; 

// Solution 2
numbers3.length = 0;

// Solution 3
// numbers3.splice(0, numbers3.length);

console.log(numbers3); // []
console.log(another1); // []
```