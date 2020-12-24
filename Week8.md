# Week 8, Ackermann Function


A function that can be implemented only through do-loops is considered primitive recursive. Examples of primitive recursion are found in the power function (2^3 = 8) and the greatest common divisor function (GCD(15) = 5). [Source](https://mathworld.wolfram.com/PrimitiveRecursiveFunction.html)



The Ackermann function introduces itself as the first example of a "well-defined total function which is computable but not primitive recursive". The Ackermann function's significance was that it was created as a counterexample to the belief that all computable functions were also primitive recursive. [Source](https://mathworld.wolfram.com/AckermannFunction.html)


    a(0,n) = n+1
    a(m+1,0) = a(m,1)
    a(m+1,n+1) = a(m, a(m+1,n))


The Ackermann function shows three lines of rules. The first line considers a pair of integers (m,n) where m=0, the second line considers where n=0, and the third line considers where m and n =/= 0. We will begin with basic examples and work our way up to more difficult demonstrations of the Ackermann function to notice any patterns that occur.

### Example 1.1: (0,0)

    a(0,0) = (0+1)
           = 1 
 
### Example 1.2: (0,1)

    a(0,1) = (1+1)
           = 2
      
### Example 1.3: (0,2)

    a(0,2) = (2+1)
           = 3
           
After trying out the first few examples of when m=0 we notice that this input will always be equal to n+1. For these cases, we do not practice recursion within the Ackermann function and the result can be answered in one step.

### Example 2.1: (1,0)

    a(1,0) = a(0,1)
           = (1+1)
           = 2
 
### Example 2.2: (2,0)

    a(2,0) = a(1,1)
           = a(0, a(1,0))
           = a(0, a(0,1))
           = a(0,2)
           = (2+1)
           = 3
           
           
    a(0,n) = n+1
    a(m+1,0) = a(m,1)
    a(m+1,n+1) = a(m, a(m+1,n))


### Example 2.3: (3,0)

    a(3,0) = a(2,1)
           = a(1, a(2,0)) -- Example 2.2 to prove a(2,0) = 3
           = a(1,3)
           = a(0, a(1,2))
           = a(0, a(0, a(1,1)))
           = a(0, a(0, a(0, a(1,0)))) -- Example 2.1 to prove a(1,0) = 2
           = a(0, a(0, a(0,2)))
           = a(0, a(0, a(0,2)))
           = a(0, a(0,3))
           = a(0,4)
           = 5
           
We do not see an immediate pattern emerging in our second set of examples, and I am starting to worry that continuing to further examples will become too complex. For this reason, we will use an [Ackermann function calculator](https://www.wolframalpha.com/widgets/view.jsp?id=fecbfa88f364df34c32702b62f11a7d9) to speed up the process.

### Example 2.4: (4,0)

    a(4,0) = 13


### Example 2.4: (5,0)

    a(5,0) = 65,533


### Example 2.4: (6,0)

    a(6,0) = (too large to represent)
    
Wow! This was unexpected. The Ackermann function is really showing us the power of expontentiality. Although the result has no obvious pattern, the results of a(m,0) where m > 3 can be shown with one expression. The result of a(4,0) can be rewritten as 2^2^2 - 3 = 13. This can be extended to a(5,0) as well by adding another '^2' to account for the increase in m, 2^2^2^2 - 3 = 65533. Now, this is where our computation ends because I do not have a calculator that can solve 2^2^2^2^2 - 3 for a(6,0), but a table of values from the [Ackermann function Wikipedia](https://en.wikipedia.org/wiki/Ackermann_function) simplifies the expression for (m,0) to (2 -> (3) -> (m-2)) - 3. In words, you can continue adding '^2' exponents to the expression 2^2^2 - 3 for each increase in m after 4.

    a(0,n) = n+1
    a(m+1,0) = a(m,1)
    a(m+1,n+1) = a(m, a(m+1,n))

### Example 3.1: (1,1)

    a(1,1) = a(0, a(1,0)) -- Example 2.1 to prove a(1,0) = 2
           = a(0,2)
           = 3

### Example 3.2: (2,2)

    a(2,2) = a(1, a(2,1))
           = a(1, a(1, a(2,0))) 
           = a(1, a(1,3)) -- Example 2.2 to prove a(2,0) = 3
           = a(1, a(0, a(1,2)))
           = a(1, a(0, a(0, a(1,1))))
           = a(1, a(0, a(0,3))) -- Example 3.1 to prove a(1,1) = 3
           = a(1, a(0,4))
           = a(1,5)
           = a(0, a(1,4))
           = a(0, a(0, a(1,3)))
           = a(0, a(0, a(0, a(1,2))))
           = a(0, a(0, a(0, a(0, a(1,1)))))
           = a(0, a(0, a(0, a(0, a(0, a(1,0))))))
           = a(0, a(0, a(0, a(0, a(0,2))))) -- Example 2.1 to prove a(1,0) = 2
           = a(0, a(0, a(0, a(0,3))))
           = a(0, a(0, a(0,4)))
           = a(0, a(0,5))
           = a(0,6)
           = 7
           
The transition from example 3.1 to 3.2 illustrates how drastic the exponential change is between even just small increments in m and n. Again, we will refer to an [Ackermann function calculator](https://www.wolframalpha.com/widgets/view.jsp?id=fecbfa88f364df34c32702b62f11a7d9) to illustrate further examples.

### Example 3.3: (3,3)

    a(3,3) = 61
    
### Example 3.4: (4,4)

    a(4,4) = (too large to represent)

Similar to example set 2, hitting values of 4 and above seem to be the breaking point of our calculator. Although, again referencing the table of values on the [Wikipedia for Ackermann function](https://en.wikipedia.org/wiki/Ackermann_function) we see a very similar expression to simplify the result of our examples. a(4,4) seems to simplify to 2^2^2^2^2^2 - 3. Further increases of m or n will increase the number of '^2's to the result. The general expression, for any input m and n, is given by (2 -> (n+3) -> (m-2)) - 3. In other words, m-4 + n+3 will give you the number of 2's needed in the result for m values above 3 and n values above 4.

### Example 4.1: (4,4)

    a(4,4) --> (4)-4 + (4)+3
           --> 7
           = 2^2^2^2^2^2^2 - 3 (7 twos)
           
### Example 4.2: (5,5)

    a(5,5) --> (5)-4 + (5)+3
           --> 9
           = 2^2^2^2^2^2^2^2^2 - 3 (9 twos)
           
### Example 4.3: (7,4)

    a(5,5) --> (7)-4 + (4)+3
           --> 9
           = 2^2^2^2^2^2^2^2^2 - 3 (9 twos)
    
This general rule allows us to represent the results of the Ackermann function in much more simplified terms without having to go through every step-by-step computation. Keep in mind that although the grammar of the results are simplified, the actual value of the results are massive and likely can not be computed on any regular calculator.
    
    
    
    
    
    
    
