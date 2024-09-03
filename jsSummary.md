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

