# Week 4, Abstract and Concrete Syntax

### Abstract Syntax
Abstract syntax represents the syntax of the source code. In our case (Assignment 1 ADD LINK), this is written by functions created by the user to represent basic mathematic operations that are otherwise available in the Haskell language. By turning them into functions we are able to use them in more ways than the basic syntax allows, such as recursion.

    Plus (Num 5) (Times (Num 4) (Minus (Num 3) (Num 1))

### Concrete Syntax
Concrete syntax represents the syntax of the input language. In our case (Assignment 1 ADD LINK), this is written by the basic operations available in the Haskell language. This is often  easier for humans to understand as it uses more familiar symbols and formatting from what we were taught.

    5 + 4 * (3 + 1)
    
### How can we use these syntaxes effectively?
We can combine these two syntaxes by creating an interpreter from concrete to abstract syntax. Such an interpreter would allow us to create expressions by writing the concrete syntax that we are familiar while still evaluating them with the freedom of abstract syntax. This allows us to create expressions that we understand while giving us the option to create our own functions within the language.

    ➜  Calculator3 git:(master) ✗ echo "1 - (gcd 6 2)" | ./Calculator
    -1
    ➜  Calculator3 git:(master) ✗ echo "abs (- 1) + 1" | ./Calculator 
    2
