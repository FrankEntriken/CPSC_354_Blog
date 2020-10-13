# Week 5, Beginning Lambda Calculus

### What is Lambda Calculus?
Lambda Calculus is a simplification on the way we write expressions that allows us to include functions and their inputs in the same line. Lambda calculus is driven by abstraction, a pillar of object oriented programming that allows for the creation and use of functions. This calculus applies functions to their arguments in a very easy and focused syntax. Lambda calculus can be viewed as the simplest way to write a program.

https://plato.stanford.edu/entries/lambda-calculus/

### How can we write in Lambda Calculus?
Lets take a familiar expression and see how we rewrite it in Lambda calculus syntax.

    int minustwo (int x) {
      return x - 2
      }
 
This simple program subtracts 2 from any integer given as the argument.

In Lambda calculus, we do not need to specify:
- types
- return statement
- parenthesis
- brackets around the expression

As you can see, Lambda calculus does a great deal to simplify a regular expression. What we are left with looks like this:

    minustwo x.x-2

The function is expressed as `minustwo x` and the `.` acts as the intermediate between the function and the body of the expression, `x-2`. In Lambda calculus, this expression is viewed as a function. We can even add a couple more characters to turn the expression into a whole program.

    (minustwo x.x-2)3
    
We can add parenthesis around our earlier expression and add the argument of the function on the outside. This one line expression now represents the definition of a function, the body of the function and the argument. It is important to note that the name of functions are not commonly used within Lambda calculus, and instead are replaced by a `λ`. This gives us an even further simplified expression.

    (λx.x-2)3



