# Week 7, Coding with Lambda Calculus...2

### Continuing LambdaNat
Now that we understand the basic syntax of LambdaNat and have even created our first function, we are now ready to modify the grammer within the interpreter to create our own syntax.

This is what LambdaNat3.cf currently looks like:

    -----------------------------------------
    -- Lambda Calculus with Natural Numbers 3
    -----------------------------------------

    Prog.   Program ::= Exp ;
    EAbs.   Exp1 ::= "\\" Id "." Exp ;
    EApp.   Exp2 ::= Exp2 Exp3 ;
    ENat0.  Exp3 ::= "0" ;
    ENatS.  Exp3 ::= "S" Exp3 ;
    EVar.   Exp4 ::= Id ;

    coercions Exp 4 ;

    token Id (letter (letter | digit | '_')*) ;

    comment "//" ;
    comment "/*" "*/" ;
    
For Assignment 2 we were tasked to add the functionality of an if-then-else clause. This clause would allow us to evaluate expressions such as

    if (x > 3) then x + 1 else x - 1
    
This is an arbitrary example, but this grammar allows us to compare variables together and create situational results. Our first step in adding this to our code is to modify LambdaNat3.cf by adding in our own expression.

    EIfThEl.   Exp5 ::= "if" Exp "=" Exp "then" Exp "else" Exp ;
    
This expression can be written as: if "variable" = "variable" then "do something" else "do something". This line shows LambdaNat to recognize expressions of this format, but we still have not shown LambdaNat *how* to understand this syntax. For this, we will need to modify the interpreter. After adding this expression to LambdaNat3.cf, this is what it looks like:

    -----------------------------------------
    -- Lambda Calculus with Natural Numbers 3
    -----------------------------------------

    Prog.   Program ::= Exp ;
    EAbs.   Exp1 ::= "\\" Id "." Exp ;
    EApp.   Exp2 ::= Exp2 Exp3 ;
    ENat0.  Exp3 ::= "0" ;
    ENatS.  Exp3 ::= "S" Exp3 ;
    EVar.   Exp4 ::= Id ;
    EIfThEl.   Exp5 ::= "if" Exp "=" Exp "then" Exp "else" Exp ;

    coercions Exp 5 ;

    token Id (letter (letter | digit | '_')*) ;

    comment "//" ;
    comment "/*" "*/" ;


This is what a portion of Interpreter.hs, evalCBN, currently looks like:

    evalCBN :: Exp -> Exp
    evalCBN (EApp e1 e2) = case (evalCBN e1) of
        (EAbs i e1') -> evalCBN (subst i e2 e1')
        e1' -> EApp e1' e2
    evalCBN (ENatS e') = ENatS (evalCBN e')
    evalCBN ENat0 = ENat0
    evalCBN x = x

We can see similarities between the two files where we initiated the grammar in LambdaNat3.cf for functions like ENat0 and ENatS. In Interpreter.hs we specify how to evaluate this grammar. Fortunately, we can create an if-then-else function within a .hs file by using the existing functionality of Haskell.

    evalCBN (EIfThEl e1 e2 e3 e4) =
      if(evalCBN e1) == (evalCBN e2)
        then evalCBN e3
        else evalCBN e4
        
The function takes in four arguments, two used for the comparison of integers and two more that act as the results of 'then' and 'else'. After adding this to Interpreter.hs, this same portion of code looks like this:

    evalCBN :: Exp -> Exp
    evalCBN (EApp e1 e2) = case (evalCBN e1) of
        (EAbs i e1') -> evalCBN (subst i e2 e1')
        e1' -> EApp e1' e2
    evalCBN (ENatS e') = ENatS (evalCBN e')
    evalCBN ENat0 = ENat0
    evalCBN (EIfThEl e1 e2 e3 e4) =
      if(evalCBN e1) == (evalCBN e2)
        then evalCBN e3
        else evalCBN e4
    evalCBN x = x
    
From here, we can practice using this syntax by generating a parser and building the interpreter. The steps for this process can be found [here](https://github.com/alexhkurz/programming-languages-2020/tree/master/Lab1-Lambda-Calculus). Once we have completed this process, we can test out our new if-then-else clause.


