
# Week 6, Coding with Lambda Calculus

### LambdaNat
LambdaNat is a small programming language that implements the basic functionality of lambda calculus. For our purposes, we will build upon its existing functionality to create more a more complex language. Throughout weeks 6 and 7 we will explore the basic functionality of LambdaNat and see how we can use it in more interesting ways.

### Beginning LambdaNat
LambdaNat can be set up using Haskell to generate a parser and build an interpreter. In-depth instructions on how to build LambdaNat can be found [here](https://github.com/alexhkurz/programming-languages-2020/tree/master/Lab1-Lambda-Calculus).

For this example, I generated and built the interpreter for LambdaNat2.cf in the LambdaNat2 folder. Once we have built the interpreter we can test it with the plus_one function that is provided in the test file plus_one.lc. The plus_one function is simple; it adds one to whatever integer is entered as the argument and returns the result. For example, plus_one(3) would return 4.

plus_one() is ran through the terminal command:

    echo "(\ x . S x) S S 0" | stack exec LambdaNat-exe
    
Lets break down this line of code to understand what is going on.


