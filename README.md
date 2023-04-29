# JavaScript

+ **JavaScript** -> is a `high level` , `single threaded`, `garbage collected `, `interpreted or just-in-time compiled`, `prototype based` `multi-paradigm` `dynamic` language with a `non-blocking event loop` made for building websites.

---


# Concepts
### High-Level
  +  It's abstracted from the low-level workings of the computer it is running on.
  +  It has great flexibility (using functions as objects) and provides a lot of different data structures to `work with without worrying about how they work internally`.
### Single-Threaded
  + Javascript engine runs on a `V8 engine` that has a memory heap and a call stack.
  + JS is a single threaded which means only one statement is executed at a time.It has `only one call stack`. Whatever is on the top of the call stack is run first.
  + `Synchronous` (or `sync`) execution usually refers to code executing in sequence. In sync programming, the program is executed line by line, one line at a time. Each time a function is called, the program execution waits until that function returns before continuing to the next line of code.
  + `Asynchronous` (or `async`) execution refers to execution that doesn’t run in the sequence it appears in the code. In async programming the program doesn’t wait for the task to complete and can move on to the next task.
  + The asynchronous implementation in Javascript is done through a `call stack`, `call back queue` and `Web API` and `event loop`.
  + Example :
    ```
    > when you make an API request. Say for example your website needs to fetch an image from a server. Should your website refuse to load other parts till the image arrives? That would be a bad user experience.
    > When call stack sees it needs to fetch an image, it pops and send it to Web API and continues executing the remaining functions.
    > The response of image request is stored in call stack queue.
    > When the call stack is empty, the event loop which is continuously running looks over the Call stack queue if it has anything. If it does, in our case the response of image request. It puts over the call stack and execute the instruction.
    > The benefit of this procedure is JavaScript need not worry about how many cores or nodes a CPU is running on. There is only single call stack for this implementation.
    ```
### Garbage-Collection
+ There’s a background process in the JavaScript engine that is called garbage collector. It `monitors` all objects and `removes` those that have become `unreachable`.

### Interpreted or JIT ( Just In Time Compiled )
+ `Compilation` ensures that the compiled code is optimized for faster execution
+ `Interpreter` ensures that code execution can immediately ensure faster startup. 
+ JavaScript engines are designed leveraging best of the both approaches & developed the Just In Time(JIT) Compilation model
+ Some of the major steps in executing a Javascript are
  ```
  > The Code is parsed to generate an intermediary format such as AST(Abstract Syntax Trees) which can be used for optimization.
  > The intermediary format is translated into machine-readable code by the interpreter to initiate the execution quickly.
  > The execution of the generated is monitored continuously & any code unit which has the scope for optimization is passed through the compilation step to generate the optimized code for the same.
  > Once, the optimized code is generated, its replaced in place of interpreter-generated code.
  > Thus ensuring the performance is improved gradually.
  ```
### Prototype-Based
+ JavaScript is a `prototype-based` language, meaning object `properties` and methods can be `shared` through generalized objects that have the ability to be `cloned` and `extended`.

### Multi-Paradigm
+ JavaScript is a multi-paradigm language, which means that we can easily `mix` a lot of different paradigms inside a simple piece of JavaScript code. We can use `object-oriented`, `procedural` and `functional` programming paradigms all at the same time in JavaScript.
  


### Dynamic
+ JavaScript is dynamic in nature , for example we don't need datatype annotations for initializing 
 ```js
  let num;

  console.log(num)  //undefined(default primitive value)

  num = 5   //int
  console.log(num)  //5

  num = "12345"   //string
  console.log(num)  //12345


 ```

### Non-Blocking-Event-Loop
 + Non-Blocking nature  simply means that js proceeds with the `execution` of  the `program instead of waiting for long I/O operations or HTTP requests`.
 + `Non-JavaScript` related code is `processed` in the background by `different threads` or by the browser which gets executed when js completes execution of the main program and when the data required is successfully fetched.
 + This way, the `long time` taking `operations` `do not block` the execution of the `remaining part` of the program. Hence the name Non-Blocking.

Example: 
  ```js
  console.log("First one to start");
   
  setTimeout(() => {
      console.log("I should wait for 3 seconds before execution");
  }, 3000);
   
  setTimeout(() => {
      console.log("I should wait for 0 seconds before execution");
  }, 0);
   
  console.log("It's time for me to end");
  ```
  ```js
  OUTPUT:
  > First one to start
  > Its time for me to end
  > I should wait for 0 seconds before execution
  > I should wait for 3 seconds before execution
  ```
---
# BASICS
### Primitives
+ Anything other than the primitives are object.
+ Example:
  + string
  + number
  + bigint
  + boolean
  + undefined
  + symbol
  + null
+ `const` -> For initializing variable that can't be reassigned instead we can use `let` and `var`.

### Functions
+ Functions are objects
+ `DECLARATION/DEFINITION` -> **Global Code Scope**
+ `EXPRESSION` -> **Local Code Scope**
+ **Definition**
  + `Function` keyword used by itself
  ```js
      function add(num1,num2)
      {
        return num1 + num2;
      }
  ```
+ **Expression**
  + Allowing functions to create as variable
  ```js
      const add = function add(num1,num2)
      {
        return num1 + num2;
      }
  ```
+  **`this`**
   + Its a keyword that references an object based on how a function has called.
   + If called globally references to `window` 
    ```js
    function hello(){
      console.log(this)       //person
    }

    const person = {}

    hello.bind(person)  //bind a function to random object
    ```
+ **Pass-By-Value & Pass-By-Reference**
  ```js
    const num = 26
    const obj = new Object()

    somefunc = (num,obj)
    // If argument is primitive like num it is passed as value ( copy is sent )
    // If argument is object it is stored in the heap and its passed by reference ( mutating same obj )
  ```
### Objects
+ Collection of `key-value` pair either declared by `{}` or by `Object()` constructor
  ```js
  const human = {
    dna: 'abcd',
    name: 'xyx',
    born: Date.now(),
    walk() {
      console.log("walking")
    }
  }
  ```
### OOP
+ JavaScript supports Object-Oriented-Programming using `class` keyword
  ```js
  class Human = {
    // invoked when instance is created
    constructor(name) {
      this.dna = 'abcd',
      this.name = name
    }
    //properties getter
    get gender(){
      return this.gender
    }
    //properties setter
    set gender(val){
      this.gender = val
    }

    // encapsulates functions as instance methods
    walk() {
      console.log("walking")
    }

  }
  ```

### Data Structures
+ **Array**
  + Dynamic collection of `indexed` items
  ```js
    const list = ['foo','bar']
  ```
+ **Set**
  + Hold collection of `unique` items
  ```js
    const uniq = new Set(list)
    const uniq2 = new WeakSet(list) //garbage collected set
  ```
+ **Map**
  + Holds a `key:value` pair
  ```js
    const dict = Map([
      ['foo': 1],
      ['bar': 2]
    ])

    const dict2 = WeakMap([
      ['foo': 1],
      ['bar': 2]
    ])                            //garbage collected map
  ```

### Promise
+ A Promise is a `proxy` for a `value not necessarily known` when the promise is `created`. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason. 
+ This lets `asynchronous methods return values like synchronous methods`: instead of `immediately returning` the final value, the asynchronous method `returns a promise` to supply the value at `some point` in the `future`.
+ A Promise is in one of these states:
  + `pending`: initial state, neither fulfilled nor rejected.
  + `fulfilled`: meaning that the operation was completed successfully.
  + `rejected`: meaning that the operation failed.
+ Example:
  ```js
    const promise = new Promise (
      (resolve,reject) => {
        // do some asyn here
        if (Success){
          resolve('success')
        }else{
          reject('failure')
        }
      }
    )

    //methods .then & .catch to handle the possible outcomes

    .then(success => {
      console.log('yay!',success)
    })

    .catch(err => {
      console.log('no!',err)
    })
  ```
+ **Async Await**
  + The keyword `async` before a function `makes` the `function return a promise`
  + The `await` keyword can only be used `inside` an `async function`.
  + The `await` keyword `makes` the `function pause` the execution and `wait for` a `resolved promise` before it continues:

    ```js
      async function myDisplay() {
        let myPromise = new Promise(function(resolve, reject) {
            resolve("I love You !!");
          });

        try{
          const result = await myPromise
        }
        catch(err){
          console.log(err)
        }
      }

      myDisplay()
    ```
### Modules
+ JavaScript modules allow you to break up your code into separate files.
+ This makes it easier to maintain a code-base.
+ **Named Export**
  ```js
  //in-line export
  export const name='shri'
  export const age=20

  //all-at-once export
  const name='shri'
  const age=20
  export {name,age}
  ```
+ **Named Import**
  ```js
  import {name,age} from "file_loc/file_name.js"
  ```
+ **Default Export**
  ```js
  const message = () => {
    const name = "Jesse";
    const age = 40;
    return name + ' is ' + age + 'years old.';
  };

  export default message;
  ```
+ **Default Import**
  ```js
  import message from "file_loc/file_name.js"
  ```

### JS-DOM
+ When a web page is loaded, the browser creates a Document Object Model of the page.
+ The HTML DOM model is constructed as a tree of Objects:
![image](https://user-images.githubusercontent.com/94846398/234317506-6f43a2d8-ddd6-4d0c-9d7b-b93edb2b68ca.png)
+ With the object model, JavaScript gets all the power it needs to create dynamic HTML:
  + Change all the HTML elements
  + Change all the HTML attributes
  + Change all the CSS styles
  + Can remove existing HTML elements and attributes
  + Can add new HTML elements and attributes
  + Can react to all existing HTML events
  + Can create new HTML events in the page
+ **Finding HTML Elements**
  ```js
  document.getElementById(id)	//Find an element by element id
  document.getElementsByTagName(name)	//Find elements by tag name
  document.getElementsByClassName(name)	//Find elements by class name
  ```
+ **Finding HTML Elements by CSS Selectors**
  ```js
  //selects based on ClassName or id or TagName
  const sub_btn = document.querySelector('submit-btn')
  const buttons = document.querySelectorAll("btn");
  ```

+ **Changing HTML Elements**
  ```js
  element.innerHTML =  new html content	//Change the inner HTML of an element
  document.getElementById("p1").innerHTML = "New text!";

  element.attribute = new value	//Change the attribute value of an HTML element
  element.setAttribute(attribute, value)	//Change the attribute value of an HTML element
  document.getElementById("element").setAttribute(id, 'name')  //Set id for element


  element.style.property = new style	//Change the style of an HTML element
  document.getElementById("p2").style.color = "blue";
  
  
  document.getElementById("myImage").src = "landscape.jpg"; //Add image source
  document.getElementById("demo").innerHTML = "Date : " + Date();   //Dynamic html content
  ```
+ **Adding and Deleting Elements**
  ```js
  document.createElement(element)	//Create an HTML element
  document.removeChild(element)	//Remove an HTML element
  document.appendChild(element)	//Add an HTML element
  document.replaceChild(new, old)	//Replace an HTML element
  document.write(text)	//Write into the HTML output stream
  ```
+ **Adding Events Handlers**
  ```js
  document.getElementById(id).onclick = function(){code}	//Adding event handler code to an onclick event
  document.getElementById("myBtn").addEventListener("click", displayDate);
  ```
+ **Form Validation**
  + If a form field (name) is empty, this function alerts a message, and returns false, to prevent the form from being submitted:
  ```js
  function validateForm() {
    let x = document.forms["myForm"]["name"].value;
    if (x == "") {
      alert("Name must be filled out");
      return false;
    }
  }
  ```
---

## Advanced Concepts

### Prototype Chain
+ The **prototype chain** is a mechanism that allows objects to inherit properties and methods from other objects. Every object can have exactly one prototype object. That prototype object can also have a prototype object, and so on, creating a chain of inherited properties and methods. The end of this chain is called the `null` prototype.
  ```js
    const animal = {
        eyes : true,
        face : true,
    }

    const dog = {
        leg : true,
    }

    Object.setPrototypeOf(dog,animal)

    consol.log(dog.eyes) //true

    Object.getPrototypeOf(dog) == animal   //true

    Object.getPrototypeOf(animal) === Object.prototype; // true

    Object.getPrototypeOf(Object.prototype) === null; // true

  ```
### Destructuring
  ```js
    // Object destructuring
    const person = {
      name: 'John',
      age: 32,
      city: 'New York',
      country: 'USA'
    };
     
    // object destructuring 
    const { name, age } = person;   // const name = person.name , const age = person.age

    // Object destructuring with alias

    const { name: firstName, age: years } = person;

    // Array destructuring
    const fruits = ['apple', 'banana', 'orange'];
    const [first, second, third] = fruits;
  ```
### Spread
  + The spread syntax `...` is a relatively new operator that was introduced in ES2018. It provides a concise way to combine objects and arrays.
    ```js
      const obj1 = {
        first: 'a',
        second: 'b',
        third: 'c',
      }
      const obj2 = {
        third: '3',
        forth: '4',
        // ... obj1 -> is also possible
      }

      // object assign -> combine one or more object with last argument as higher priority
      const obj12 = Object.assign( {}, obj1, obj2 )
      // spread operator
      const obj12  =  { ...obj1, ...obj2}
      obj12.third // '3'

      // combining arrays
      const arr1 = [1, 2, 3];
      const arr2 = [4, 5, 6];
      const arr3 = [...arr1, ...arr2];
    ```

### Optional Chaining
+ Optional chaining `?` is a relatively new operator that was introduced in ES2020.
+  It allows you to call object properties safely, without throwing an error.
+   When calling properties without this operator, you many crash your application with the error `Cannot read property 'foo' of undefined`.
  ```js
    const person = { };

    const dude = person.name;
    console.log(foo); // Uncaught TypeError: Cannot read property 'bar' of undefined

    const dude = person?.name; // undefined
  ```

### Nullish Coalescing
+ Nullish coalescing is a relatively new operator **`??`** that was introduced in ES2020.
+  It is similar to the logical OR operator ||, but it only returns the right-hand side if the left-hand side is null or undefined.
+ **TRUTHY LIST**
  + `true`
  + `{}`
  + `[]`
  + `42`
  + `"0"`
  + `"false"`
  + `new Date()`
  + `-42`
  + `12n`
  + `Infinity`
+ **FALSY LIST**
  + `null`
  + `undefined`
  + `0`
  + `''`
  ```js
    const foo = null ?? 'bar';
    console.log(foo); // 'bar'

    const foo = 0 ?? 'bar';
    console.log(foo); // 0
  ```

### Higher Order Functions
+ A higher order function is a function that takes a function as an argument, or returns a function. 
+ They are commonly used in functional programming, and are a powerful tool for abstracting away complexity.
  ```js
    // A function that takes a function as an argument
    function add(x, y) {
      return x + y;
    }
    function subtract(x, y) {
      return x - y;
    }
    function math(x, y, operator) {
      return operator(x, y);
    }

    math(5, 2, add); // 7

    // A function returning another function

    function fun(){
      return function(message){
        return 'Said...' + message
      }
    }

    const fn = fun()
    fn('hello')   // 'Said...hello
  ```

### Closures
+ A closure is a function that has access to the parent scope, even after the parent function has closed.
+  JS will automatically store the state of a closure in the heap memory, even after the parent function has returned.
+   This behavior makes them useful for encapsulating private variables.
+ Its not just a function, its a function combined with outer state
+ Used for **DATA ENCAPSULATION**
```js
    // lexical environment -> free variable -> this is closure
    const state = 'happpy'

    function whatstate () {
      return `state is ${state}`  //captures
    }

    // no external data -> not a closure -> data (a,b) only stored in stack memory until function popped back of call stack
    function add(a,b){
      return a+b
    }

    function outer() = {
      let x = 1
      function inner() = {
        x = x + 1
      }
      return inner
    }

    let increment = outer()
    increment() // x = 2
    increment() // x = 3
  ```

### More On Arrays
+ Create a Range of Numbers
  ```js
    const range = Array(100).fill(0).map((_, i) => i + 1);
    // OR
    const range = [...Array(100).keys()];
  ```
+ Remove Duplicates from an Array
  ```js
    const unique = [...new Set(arr)];
  ```
+ Get a Random Element
  ```js
    const random = arr[Math.floor(Math.random() * arr.length)];
  ```
+ Loop over a Key-Value Pair
  ```js
    for(const [i, val] of arr.entries()) {
        console.log(i, val);
    }
  ```
+ `forEach()`
  + It calls a function for each element in an array.
  ```js
    let sum = 0;
    const numbers = [65, 44, 12, 4];
    numbers.forEach(myFunction);

    function myFunction(item) {
      sum += item;
    }
  ```
+ `map()`
  + Creates a new array from calling a function for every array element.
  + Does not execute the function for empty elements.
  + Does not change the original array.
  ```js
    const numbers = [4, 9, 16, 25];
    const newArr = numbers.map(Math.sqrt)
  ```
+ `filter()`
  +  Creates a new array filled with elements that pass a test provided by a function.
  +  Does not execute the function for empty elements.
  +  Does not change the original array.
  ```js
   const ages = [32, 33, 16, 40];
   const result = ages.filter(checkAdult);

   function checkAdult(age) {
     return age >= 18;
   }
  ```
+ `find()`
  + It returns the value of the first element that passes a test.
  + It executes a function for each array element.
  + It returns undefined if no elements are found.
  + It does not execute the function for empty elements.
  + It does not change the original array.
  ```js
    const ages = [3, 10, 18, 20];

    function checkAge(age) {
      return age > 18;
    }

    function myFunction() {
      document.getElementById("demo").innerHTML = ages.find(checkAge);
    }
  ```
+ `findIndex()`
  + It method executes a function for each array element.
  + It method returns the index (position) of the first element that passes a test.
  + It method returns -1 if no match is found.
  + It method does not execute the function for empty array elements.
  + It method does not change the original array.
  ```js
    const ages = [3, 10, 18, 20];

    ages.findIndex(checkAge); // 3 -> ages[3] = 18

    function checkAge(age) {
      return age > 18;
    }
  ```
+ `reduce()`
  + It method executes a reducer function for array element.
  + It method returns a single value: the function's accumulated result.
  + It method does not execute the function for empty array elements.
  + It method does not change the original array.
  ```js
    const numbers = [175, 50, 25];

    document.getElementById("demo").innerHTML = numbers.reduce(myFunc);

    function myFunc(total, num) {
      return total - num;
    }
  ```
---
