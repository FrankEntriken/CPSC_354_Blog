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
    
https://en.wikipedia.org/wiki/Ackermann_function
Wow! This was unexpected. The Ackermann function is really showing us the power of expontentiality. Although the result has no obvious pattern, the results of a(m,0) where m > 3 can be shown with one expression. The result of a(4,0) can be rewritten as 2^2 - 3 = 13. This can be extended to a(5,0) as well by adding another "^2" to account for the increase in m, 2^2^2 - 3 = 65533. Now, this is where our computation ends because I do not have a calculator that can solve 2^2^2^2 - 3 for a(6,0), but wikipedia simplifies the expression for (m,0) to (2 -> (3) -> (m-2)) - 3. In words, you can continue adding "^2" exponents to the expression for each increase in m starting at 4.

           
           
           
