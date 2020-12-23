# Week 8, Ackermann Function

https://mathworld.wolfram.com/PrimitiveRecursiveFunction.html
A function that can be implemented only through do-loops is considered primitive recursive. Examples of primitive recursion are found in the power function (2^3 = 8) and the greatest common divisor function (GCD(15) = 5).

https://mathworld.wolfram.com/AckermannFunction.html
The Ackermann function introduces itself as the first example of a "well-defined total function which is computable but not primitive recursive". The Ackermann function's significance was that it was created as a counterexample to the belief that all computable functions were also primitive recursive.


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

### Example 2.1: (0,0)

    a(1,0) = a(0,1)
           = (1+1)
           = 2
 
### Example 2.2: (0,1)

    a(2,0) = a(1,1)
           = a(0, a(1,0))
           = a(0, a(0,1))
           = a(0,2)
           = (2+1)
           = 3
           
           
    a(0,n) = n+1
    a(m+1,0) = a(m,1)
    a(m+1,n+1) = a(m, a(m+1,n))


### Example 2.3: (0,2)

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
           
 We do not see an immediate pattern emerging

           
           
           
