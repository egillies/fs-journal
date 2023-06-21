# Intro to JavaScript

1.  Which keywords are used to declare a variable in JavaScript?

    let, const, var (old)

2.  What is the definition of a function?

    block of code used to perform a particular task

3.  What are the `SOLID` principles?

    single responsibility, open closed, liskov substistution, interface integration, dependency inversion

4.  Given this array: How could you remove the `pineapple`?

    ```js
    let fruit = ["apple", "banana", "pineapple", "orange", "strawberry"];
    ```

    splice method

5.  Given these two objects: How could you add each to the others friends arrays?

    ```js
    let you = {
      name: "You",
      hair: true,
      friends: [],
    };
    let them = {
      name: "Them",
      hair: false,
      friends: [],
    };
    ```

    array.push

6.  Give an example of a JavaScript `Conditional`:

    if (hour < 12) {
    console.log("good morning")
    }

7.  What is the main difference between `parameters` and `arguments`?

    a parameter is a name created in a function definition
    an argument is the value each function derives from the parameter when the function is invoked

8.  Instead of writing everything to the console, what is a better way to debug your code?

    testing it in the web browser

9.  What is the difference between a `primitive` value and a `reference` value?

    primitive value is data that is not a function and has no methods or properties
    reference value inclues array, object, and function

10. Demonstrate a loop that prints the numbers between -100 and 100?

    for(let i = 0; i < 101; i++);
