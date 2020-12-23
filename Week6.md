
# Week 6, Coding with Lambda Calculus

### LambdaNat
LambdaNat is a small programming language that implements the basic functionality of lambda calculus. For our purposes, we will build upon its existing functionality to create more a more complex language. Throughout weeks 6 and 7 we will explore the basic functionality of LambdaNat and see how we can use it in more interesting ways.

### Beginning LambdaNat
LambdaNat can be set up using Haskell to generate a parser and build an interpreter. In-depth instructions on how to build LambdaNat can be found [here](https://github.com/alexhkurz/programming-languages-2020/tree/master/Lab1-Lambda-Calculus).

For this example, I generated and built the interpreter for LambdaNat2.cf in the LambdaNat2 folder. Once we have built the interpreter we can test it with the plus_one function that is provided in the test file plus_one.lc. The plus_one function is simple; it adds one to whatever integer is entered as the argument and returns the result. For example, plus_one(3) would return 4.

plus_one() is ran through the terminal command:

    echo "(\ x . S x) S S 0" | stack exec LambdaNat-exe
    
Lets break down this line of code to understand what is going on.

    echo
    
Echo is built in to Mac and Windows terminals as a simple command that displays a line of text/string that is being passed as an argument. This will allow us to see the result of the function in the terminal.


    "(\ x . S x) ..."
    
This first bit of code is the function plus_one(). The syntax \x. represents lambda x, λx.
This line will return the argument, x, with an S in front of it. This syntax of representing numbers using S's and 0's is from our first Assignment when we built a calculator in Haskell. Simply put, a 0 is a 0, S 0 is 1, S S 0 is 2, S S S 0 is 3, and so forth. By returning the argument with an S in front, we are adding one.

    "... S S 0"
    
The last line within the quotations is the argument being passed into the plus_one() function. S S 0 represents a 2. What we should expect as the output from this function is a 3, or S S S 0.

    | stack exec LambdaNat-exe
    
The | character, or pipe, allows us to run a line of code into another. Stack exec LambdaNat-exe runs an argument through the LambdaNat interpreter. In our case, the program "(\ x . S x) S S 0" is being run through the interpreter, allowing us to evaluate this unique syntax within a language that understands it.

    ➜  LambdaNat2 git:(master) ✗ echo "(\ x . S x) S S 0" | stack exec LambdaNat-exe

     Input:
    (\ x . S x) S S 0

    [Abstract Syntax]

    Prog (EApp (EAbs (Id "x") (ENatS (EVar (Id "x")))) (ENatS (ENatS ENat0)))

     Output:
    S S S 0
    
This is what our terminal looks like after running the entire line in the terminal. LambdaNat recognizes the input, generates the syntax that it can understand, and outputs the expected result, S S S 0.
    
    
    
