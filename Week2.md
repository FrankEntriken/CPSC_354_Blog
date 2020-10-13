# Week 2, Learning Haskell

### Loading files

Files can be loaded within Haskell using

    :load file_name

Once the file is loaded, the functions that are established within the file will now be available to the user

### Creating meaningful functions

    multiply.hs
    mult x y = x * y
   
    Prelude> :load addition.hs
    [1 of 1] Compiling Main             ( addition.hs, interpreted )
    Ok, one module loaded.
    *Main>
    *Main> mult 6 7
    42
    *Main>

The file multply.hs defines the function `mult` which multiplies two numbers together. After loading the file we are able to use the `mult` function.
Now, the function `mult` may seem completely unnecessary; we know that Haskell can already handle multiplication using the `*` operator. But with some creativity we can establish some more complex functions that involve multiples steps.

    fibonnaci.hs
    fib 0 = 0
    fib 1 = 1
    fib n = fib (n-1) + fib (n-2)
    
    Prelude> :load fib.hs
    [1 of 1] Compiling Main             ( fib.hs, interpreted )
    Ok, one module loaded.
    *Main> 
    *Main> fib 10
    55
    *Main> fib 16
    987
    *Main> fib 20
    6765
    *Main>

The file fibonnaci.hs defines the function `fib` which takes in a positive integer and returns the corresponding number of the fibonacci sequence. Lets break this function down to understand each step clearly.

    fib 0 = 0
    
This step defines the case for an input of 0. This case could read: if 0, return 0. This step needs to be defined so that the recursive expression eventually stops.

    fib 1 = 1

Just as we defined the case for 0, we have to do so for 1: if 1, return 1.
    
    fib n = fib (n-1) + fib (n-2)
    
This expression will cover for all other positive integers, n. When a positive integer other than 0 or 1 is input, the expression will continuosly call upon itself until it reaches the earlier expressions. Once it reaches these expressions, instead of calling upon itself it will instead return 0 or 1.
