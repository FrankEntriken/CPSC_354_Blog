# Week 3, Numbers and Error

### Natural Numbers
Natural numbers are all positive integers, including 0.

    x = 0, x > 0

### Positive Numbers
Positive numbers are all positive integers, excluding 0.

    x > 0
    
### Negative Numbers
Negative numbers are all negative integers, excluding 0.

    x < 0

### Error checking
When creating functions it is necessary to understand what numbers are allowed as an input. Often times, only implementing positive numbers is the easiest path towards completing a mathematical function, but this is a very limited range of numbers. If only positive numbers are considered, what happens when the user inputs outside this set of numbers?

Lets take a look at what happens when we create functions that do not account for 0.

    divv x y =
      if x < y
        then 0
        else (divv (x - y) y) + 1
    
    Prelude> :load divison.hs 
    [1 of 1] Compiling Main             ( divison.hs, interpreted )
    Ok, one module loaded.
    *Main> 
    *Main> div_q 5 2
    2
    *Main> div_q 5 3
    1
    *Main> div_q 6 3
    2
    *Main> div_q 3 0
    *** Exception: stack overflow
    *Main> 

The function `divv` implements basic divison by returning how many times the divisor can be subtracted from the dividend. Although the function works as intended, we see that in cases where the divisor is 0 we are returned with a stack overflow error. This is because we have not created a case for a divisor of 0 and instead we let Haskell interpret the error. It is better to catch all errors within the function you create so that there is a clear error description for the user to understand.

A more successful implementation of `divv` would include a case for catching 0 in the divisor.

    divv x 0 = error "The divisor can not be zero"
    divv x y =
      if x < y
        then 0
        else (divv (x - y) y) + 1
        
    *Main> :load divison.hs 
    [1 of 1] Compiling Main             ( divison.hs, interpreted )
    Ok, one module loaded.
    *Main> 
    *Main> divv 3 0
    *** Exception: The divisor can not be zero
    CallStack (from HasCallStack):
      error, called at divison.hs:1:12 in main:Main
    *Main> 

With the addition of the new first line we see that cases with 0 in the divisor show a clear message to the user why their input is not valid. This is a much more customized error message than the standard stack overflow exception which does not tell the user exactly what is wrong within the function.

*** Add fractions example??
