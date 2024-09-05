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

Here is your code formatted in `.md` (Markdown) format, along with explanations for each point:

### Combining Arrays
```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const arr3 = arr1.concat(arr2);
console.log(arr3); // [1, 2, 3, 4, 5, 6]
```
- `concat()` merges two or more arrays into a single array.

### Spread Operator for Arrays
```javascript
const arr4 = [...arr1, ...arr2];
console.log(arr4); // [1, 2, 3, 4, 5, 6]
```
- The spread operator (`...`) can also be used to combine arrays. It is more concise and versatile.

### Copying an Array
```javascript
const arr7 = [...arr4];
```
- Using the spread operator, you can create a shallow copy of an array.

### Slicing an Array
```javascript
const arr5 = arr4.slice(1, 3);
console.log(arr5); // [2, 3]
const arr6 = arr4.slice(2);
console.log(arr6); // [3, 4, 5, 6]
```
- `slice()` returns a portion of an array based on start and end indices. The original array remains unchanged.

### Iterating Over an Array
```javascript
arr4.forEach((item, index) => {
  console.log(`Index ${index} has value ${item}`);
});

for (let i of arr4) {
  console.log(i);
}
```
- `forEach()` iterates over each element, giving access to both the value and index.
- The `for...of` loop is another method to iterate over array elements.

### Joining an Array into a String
```javascript
const arr8 = arr4.join("-");
console.log(arr8); // 1-2-3-4-5-6 //string
```
- `join()` merges all elements of an array into a string, separated by the specified character.

### Splitting a String into an Array
```javascript
const course = "Java Script";
const chars = course.split(" ");
console.log(chars); // ["Java", "Script"]
```
- `split()` breaks a string into an array based on a delimiter.

### Method Chaining
```javascript
const messege = "Hello World";
const newMessege = messege
  .toUpperCase()
  .split(" ")
  .join("-");
console.log(newMessege); // HELLO-WORLD
```
- You can chain multiple methods together for more concise operations. Here, we chain `toUpperCase()`, `split()`, and `join()`.

### Sorting and Reversing Arrays
```javascript
const arr9 = ['a', 'c', 'b', 'd'];
arr9.sort();
console.log(arr9); // ['a', 'b', 'c', 'd']
arr9.reverse();
console.log(arr9); // ['d', 'c', 'b', 'a']
```
- `sort()` arranges array elements in ascending order (lexicographically for strings).
- `reverse()` reverses the order of the array.

### Sorting an Array of Objects
```javascript
let employees = [
    { name: "John", id: 1 },
    { name: "Jane", id: 2 },
    { name: "Doe", id: 3 },
    { name: "Alice", id: 4 }
];
employees.sort((a, b) => {
    const lowerA = a.name.toLowerCase();
    const lowerB = b.name.toLowerCase();
    if (lowerA < lowerB) return -1;
    if (lowerA > lowerB) return 1;
    return 0;
});
console.log(employees);
```
- When sorting objects, you must define a custom comparison function, as shown here.

### Filtering Objects
```javascript
const objectFiltered = employees.filter(employee => {
    return employee.id > 2;
});
```
- `filter()` returns a new array with all elements that pass the test provided by the function.

### Testing Elements in an Array
```javascript
const arr10 = [1, 2, 3, 4, 5];
const allPositive = arr10.every(value => value > 0);
console.log(allPositive); // true
const allEven = arr10.every(value => value % 2 === 0);
console.log(allEven); // false

const someEven = arr10.some(value => value % 2 === 0);
console.log(someEven); // true
```
- `every()` checks if **all** elements in an array pass a test.
- `some()` checks if **at least one** element passes the test.

### Filtering an Array
```javascript
const arr11 = [1, 2, 3, 4, 5];
const filtered = arr11.filter(value => value % 2 === 0);
console.log(filtered); // [2, 4]
```
- `filter()` creates a new array with elements that satisfy a condition.

### Mapping an Array
```javascript
const arr12 = [1, 2, 3, 4, 5];
const mapped = arr12.map(value => value * 2);
console.log(mapped); // [2, 4, 6, 8, 10]

const arr13 = ['a', 'b', 'c', 'd', 'e'];
const mapped2 = arr13.map(value => value.toUpperCase());
console.log(mapped2); // ['A', 'B', 'C', 'D', 'E']
```
- `map()` creates a new array by applying a function to each element in the array.

### Mapping Objects
```javascript
const employees = [
    { name: "John", id: 1 },
    { name: "Jane", id: 2 },
    { name: "Doe", id: 3 },
    { name: "Alice", id: 4 }
];
const mapped3 = employees.map(employee => {
    return {
        ...employee, // Copying original object properties
        name: employee.name.toUpperCase()
    };
});
console.log(mapped3);
```
- You can use `map()` on arrays of objects to modify or transform properties in each object.

### Reducing an Array
```javascript
const arr14 = [1, 2, 3, 4, 5];
let sum = arr14.reduce((accumulator, currentValue) => {
    return accumulator + currentValue;
}, 0); 
console.log(sum); // 15
```
- `reduce()` applies a function to accumulate a single value from the elements of the array. Here, it calculates the sum of the array.

Here is your code formatted in `.md` (Markdown) format with explanations:

## JavaScript Functions, Arguments, and More Explained

### 1. **Function Declaration**
```javascript
function SayHi() {
    console.log('Hi');
}
```
- Function declarations are hoisted to the top of the code, meaning you can call the function before its definition.
- Example:
```javascript
SayHi(); // Calls the function and outputs: Hi
```

### 2. **Hoisting**
- **What is hoisting?**
  - Hoisting is the process of moving function and variable declarations to the top of their scope before code execution.
  - JavaScript's engine performs this before running the code, which is why you can call functions declared this way before the actual declaration.

### 3. **Function Expression**
```javascript
let SayHi = function() {
    console.log('Hi');
};
```
- In this case, the function is stored in a variable. This is called a **function expression** or **anonymous function**.
- Unlike function declarations, function expressions are **not hoisted**.

### 4. **Arguments and Function Parameters**
```javascript
function SayHi(name) {
    console.log('Hi ' + name);
}
```
- Functions can accept parameters. You can pass more or fewer arguments than expected:
  - Passing extra arguments: They are ignored.
  - Passing fewer arguments: The missing ones will be `undefined`.

Example:
```javascript
SayHi('John', 'Doe'); // Outputs: Hi John
SayHi(); // Outputs: Hi undefined
```

### 5. **Arguments Object**
```javascript
function multiply(a, b) {
    let product = 1;
    for (let i = 0; i < arguments.length; i++) {
        product *= arguments[i]; 
    }
    console.log(arguments); // Logs: [Arguments] { '0': 2, '1': 3 }
    return product;
}
multiply(2, 3); // Outputs: 6
```
- The `arguments` object is an array-like object that holds all arguments passed to a function. It allows functions to handle a variable number of arguments.

### 6. **Rest Parameter**
```javascript
function multiply(...args) {
    return args.reduce((acc, curr) => acc * curr, 1);
}
console.log(multiply(2, 3, 4)); // Outputs: 24
```
- The rest parameter (`...args`) allows you to represent an indefinite number of arguments as an array.

### 7. **Default Parameter**
```javascript
function SayHi(name = 'John') {
    console.log('Hi ' + name);
}
SayHi(); // Outputs: Hi John
```
- Functions can have default parameters. If no argument is provided, the default value is used.

### 8. **Getters and Setters**
```javascript
let person = {
    firstName: 'John',
    lastName: 'Doe',
    get fullName() {
        return this.firstName + ' ' + this.lastName;
    },
    set fullName(value) {
        let parts = value.split(' ');
        this.firstName = parts[0];
        this.lastName = parts[1];
    }
};
console.log(person.fullName); // Outputs: John Doe
person.fullName = 'salma hamed';
console.log(person.fullName); // Outputs: salma hamed
```
- **Getters** allow you to access object properties in a cleaner way.
- **Setters** allow you to assign values to properties indirectly.

### 9. **Try and Catch**
```javascript
try {
    let x = 1;
    x = y + 1;
} catch (error) {
    console.log(error); // Outputs: ReferenceError: y is not defined
}
```
- The `try` block lets you test code for errors. The `catch` block handles the error if it occurs.

### 10. **Throwing Errors**
```javascript
try {
    let x = 1;
    throw new Error('Something went wrong');
} catch (error) {
    console.log(error); // Outputs: Error: Something went wrong
}
```
- You can explicitly throw an error using `throw`. This can be useful for handling custom error scenarios.

### 11. **Local and Global Scope**
```javascript
let x = 1; // Global scope
function Add() {
    let y = 2; // Local scope
    console.log(x + y); // Accessible inside the function
}
Add(); // Outputs: 3
```
- Variables declared outside any function have **global scope**.
- Variables declared within a function have **local scope**.

### 12. **Let vs Var**
- `let` has block scope, while `var` has function scope.
- `let` is generally preferred over `var` as it avoids issues like accidental redeclarations.
- `var` is hoisted to the top of its function, while `let` is hoisted to the top of the block but not initialized.

### 13. **The `this` Keyword**
```javascript
let person2 = {
    name: 'John',
    walk() {
        console.log(this);
    }
};
person2.walk(); // Outputs: { name: 'John', walk: [Function: walk] }
```
- `this` refers to the object that is calling the function. In this case, it refers to `person2`.

### 14. **Arrow Functions**
```javascript
let square = number => number * number;
```
- Arrow functions provide a shorter syntax for function expressions.
- **Important:** Arrow functions do not have their own `this` context. They inherit `this` from their surrounding scope.
- Arrow functions do not have an `arguments` object.

The `bind()` method in JavaScript is used to create a new function that, when called, has its `this` keyword set to the provided value. This is useful when you want to control or change the context (`this`) in which a function executes.

### 15. **How `bind()` Works**

Normally, the value of `this` inside a function is determined by how the function is called:
- If a method is called as a property of an object, `this` refers to that object.
- However, if a function is assigned to a variable or passed around as a callback, the `this` value might get lost.

With `bind()`, you can fix the value of `this` for a function, ensuring it refers to the correct object even when called outside of its usual context.

### Example without `bind()`

```javascript
let person = {
    name: 'John',
    walk() {
        console.log(this.name);
    }
};

person.walk(); // Outputs: John

let walk = person.walk;
walk(); // Outputs: undefined, because `this` is no longer referring to the `person` object
```
In the above example, `walk` is assigned to a variable. When calling `walk()`, it no longer refers to `person`, and `this.name` is `undefined`.

### Example with `bind()`

```javascript
let person = {
    name: 'John',
    walk() {
        console.log(this.name);
    }
};

let boundWalk = person.walk.bind(person);
boundWalk(); // Outputs: John
```
In this case, `person.walk.bind(person)` creates a new function (`boundWalk`) where `this` is permanently set to the `person` object. No matter where or how you call `boundWalk`, `this` will always refer to `person`.

### Key Points:
1. **Permanent Binding:** The `bind()` method does not change the original function; it returns a new function with a permanently bound `this`.
2. **Partial Application (Optional Arguments):** You can also use `bind()` to pass in some arguments to the function ahead of time, which is known as **partial application**.

### Example with Partial Application:
```javascript
function greet(greeting, name) {
    console.log(greeting + ', ' + name);
}

let greetJohn = greet.bind(null, 'Hello');
greetJohn('John'); // Outputs: Hello, John
```
Here, `bind(null, 'Hello')` creates a new function (`greetJohn`) where the first argument (`greeting`) is fixed to `'Hello'`. You only need to provide the second argument (`name`) when calling `greetJohn()`.
