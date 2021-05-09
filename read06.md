# function 
>A JavaScript function is a block of code designed to perform a particular task.

>A JavaScript function is executed when "something" invokes it (**calls it**).

>A function definition (also called a function declaration, or function statement) consists of the function keyword, followed by:
- The name of the function.
- A list of parameters to the function, enclosed in parentheses and separated by commas.
- The JavaScript statements that define the function, enclosed in curly brackets, {...}.
##
# JavaScript Function Syntax
>
```
function name(parameter1, parameter2, parameter3) {
  // code to be executed
}
```
>Function parameters are listed inside the parentheses () in the function definition.

>Function arguments are the values received by the function when it is invoked.

>Inside the function, the arguments (the parameters) behave as local variables.

# Function Return
>When JavaScript reaches a return statement, the function will stop executing.
If the function was invoked from a statement, JavaScript will "return" to execute the code after the invoking statement.
Functions often compute a return value. The return value is "returned" back to the "caller":
```
Example
Calculate the product of two numbers, and return the result:
>
var x = myFunction(4, 3);   // Function is called, return value will end up in x
function myFunction(a, b) {
  return a * b;             // Function returns the product of a and b
}
>
The result in x will be:
> 12
```

# Function expressions
```
const square = function(number) { return number * number }
var x = square(4) // x gets the value 16
```

# Calling functions
>Defining a function does not execute it. Defining it names the function and specifies what to do when the function is called.
>Calling the function actually performs the specified actions with the indicated parameters. For example, if you define the function square, you could call it as follows:

```
square(5);
```
```
console.log(square(5));
/* ... */
function square(n) { return n * n }
 > result =25 
 ```