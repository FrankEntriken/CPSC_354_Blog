# Week 9, Beginning LambdaFun

### Running LambdaFun
Instructions on how to run LambdaFun can be found [here](https://github.com/alexhkurz/programming-languages-2020/tree/master/Lab2-Lambda-Calculus/LambdaFun)

### Basics
LambdaFun supports all basic mathematical operations.

    ➜  LambdaFun git:(master) ✗ stack exec LamFun
    Found settings file ... setting language to LamMem

      $$$$\        $$$$$$$$\                     
        $$ \       $$  _____|                    
         $$ \      $$ |    $$\   $$\ $$$$$$$\  
         $$$ \     $$$$$\  $$ |  $$ |$$  __$$\ 
        $$ $$ \    $$  __| $$ |  $$ |$$ |  $$ |
       $$ / $$ \   $$ |    $$ |  $$ |$$ |  $$ |
     $$$ /   $$$\  $$ |    \$$$$$$  |$$ |  $$ |
     \___|   \___| \__|     \______/ \__|  \__|

    Welcome to λFun v3.14.1 ...
    λ 
    λ 
    λ  3 + 3;;

    6
    λ 1 - 2;;

    -1
    λ 9 / 3;;

    3
    λ 5 * 5;;

    25
    
LambdaFun supports the creation of variables.

    λ val b = a;;
    λ b;;

    3
    λ a;;

    3
    λ b + a;;

    6
    
LambdaFun supports the creation of lists.

    λ val abc = [1,2,3];;
    λ abc;;

    [1, 2, 3]
    
LambdaFun has cool tools such as `:env`, `:info`, and `:tree`.

    λ val abc = [1,2,3,"string"];;
    λ abc;;

    [1, 2, 3, "string"]
    λ 
    λ :env
    Built in functions:
    !, !=, *, +, -, /, <, <=, ==, >, >=, head, int?, mod, new, print, println, tail, ~
    Env:
    abc -> [1, 2, 3, "string"]
    Memory:

    λ 
    λ :info abc
    Val_ "abc" 
        ( Cons_ ( Number_ 1 ) 
            ( Cons_ ( Number_ 2 ) 
                ( Cons_ ( Number_ 3 ) 
                    ( Cons_ ( StrLit_ "string" ) Nil_ )
                )
            )
        )
    λ 
    λ :tree 3+3-5*99;;
    Calculate_ 
        ( App_ 
            ( App_ ( Variable_ "-" ) 
                ( App_ 
                    ( App_ ( Variable_ "+" ) ( Number_ 3 ) ) ( Number_ 3 )
                )
            ) 
            ( App_ 
                ( App_ ( Variable_ "*" ) ( Number_ 5 ) ) ( Number_ 99 )
            )
        )
    λ 

`:env` shows us a full view of our stack in which we created the list `abc`. `:info` shows us all we need to know about our list. It shows us every element within the list as well as the type of variable that the element is while ending indicating the end of the list with `Nil_`. `:tree` takes an expression and outputs the computation of the expression as an abstract syntax tree. These tools can be useful during periods of debugging to find errors within longer blocks of code than these examples.


In my opinion, LambdaFun's most useful features is the ability to load files that extend the basic interpreter within the Terminal. This allows a user to create their own grammar, load it into LambdaFun and use their new features in real time without the need to run files every time they want to test a program. Of course, runnning many lines of code at once is necessary for larger projects, but for more simple purposes I have found it incredibly useful being able to toy around in LambdaFun in order to understand how your grammar interacts with the language.


[Assignment 3](https://github.com/alexhkurz/programming-languages-2020/blob/master/assignment-3.md) extended the basic LambdaFun language to allow for linked lists.  Linked lists are different from normal lists because you can change the pointer of one element manually by assigning an address to point to. A crude illustration of a linked list would look something like this.

    [value, address] --> [value, address] --> [value, address] -->
    [1, address <0>] --> [2, address <1>] --> [3, address <2>] -->
          A                     B                   C

Each element within the list is a pair of information, a value and an address. In this example, element A points to element B which points to Element C which points back to element A. This is a circular linked list; a linked list in which the last element always points back to the first element, forming a 'circle'.






