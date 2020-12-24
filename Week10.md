# Week 10, Indexing round-robin.lc

I enjoyed all of the assignments within this class. They were sequential, Assignment 1 fed into Assignment 2 and so on, and felt challenging enough that I was left satisfied upon completion. Although, I felt a minor exception to this when completing the last assignment, Assignment 3 part 2. I felt like I spent the majority of my time learning and understanding LambdaFun when it came to creating memory and seeing how I could interact with it using `:env` and not so much time interacting with the code. When it came to the functions, I ended up finishing those much more quickly as I only had to write a few lines of code. Now, this may just be me but I would have enjoyed a slightly longer assignment that included a couple more in-depth functions. I had the idea to continue round-robin.lc and create some of my own functions that I think would be useful when interacting with a circular linked list. Although, I soon realized that LambdaFun does not support recursion in the same way that LambdaNat allowed us to, which meant that the functions I created would not run. Instead of scrapping this idea, I will instead continue to show off my index function that I created and how this would be useful to the other functions. I will show you what went wrong and how I had hoped `index` would work within LambdaFun.

### `index`

    val index = \p. \a.
        case p == 0 of {
          true -> a,
          false -> index (p-1) (next a)
    };;

The index function would allow us to return the address of the element within a certain location in the circular linked list. The function would take in an integer, acting as the location of the desired element, and a circular linked list. For example, a regular list in python could be parsed using list[0] to return the first element of the list. The integer would determine what element of the list would be returned based on its location in the list. `index` recursively calls itself, decreasing the value of e every time the current element moves to the next. When e is equal to zero, the current element a will be in the desired position of the circular linked list and return this position. From here, the user could interact with this element with any of the other functions. 



`index` does not run because it recursively calls itself. It seems to me that LambdaFun does not have the functionality for recursion because I am met with this error:

    λ insert 1 a;;

    "a" is not defined
    CallStack (from HasCallStack):
      error, called at src/Environment.hs:24:16 in LamFun-3.14.1-HB5izHlLIvCGGFpWbUCpOd:Environment
    λ
    
I did a lot of testing and poking around and, although it is hard to tell, I believe that LamdaFun is erroring out when index is being recursively called within the false case.



This is what I would hope the index function would look like when called on a circular list.

    EXAMPLE CIRCULAR LIST 'a'
    [1, <address 0>] --> [3, <address 1>] --> [66, <address 2>] -->

    USING INDEX
    λ index 0 a;;
    
    <address 0>
    λ index 1 a;;
    
    <address 1>
    λ get(index 1 a);;
    
    3
    λ next(index 2 a);;
    
    <address 0>
    λ update 2 (index 2 a);;
    
    [2, <address 2>]
    λ

If the user were to index past the 'last item' in a circular linked list, it would index back to the beginning like expected.

The functionality of an index function would allow us to add much more accuracy to all of the other functions we have created by simply introducing the `p` variable to the argument. Adding a `p` variable would let the user specify where in the list they would like this function to occur, allowing them to choose their current element of the list instead of relying on many `next`s put together. As of now, if you had a circular linked list of 10 elements, you would need to string together 7 `next`s in order to access the 8th element. With `index`, we would simply specify the element within the argument of the function. We could update the existing functions as so:

    -- it is not necessary to change next
    val next = \a.
        case !a of { [e',a'] -> a' };;

    EXCLAIMER: It would be easy to add in a line at the start of every function along the lines of, a = (index p a) but this does not seem to be supported within LambdaFun
    
    -- input: clist, position
    val getP = \a. \p.
        case !(index p a) of { [e',(index p a)'] -> e' };;

    -- input: value, clist, position
    val insertP = \e. \a. \p.
        let val b = newCList e in
        b := [get b, next (index p a)];
        a := [get (index p a), b];;

    val deleteP = \a.
        a := [get (index p a), next (next (index p a))];;

    val updateP = \e. \a.
        (index p a) := [e, next (index p a)];;

By changing every occurence of a circular linked list to its index we can now reference specific positions within the list.


### Difficulties
1. Adding recursive functionality to LambdaFun. Whether or not this is possible, I do not know.

2. Adding more functionality means adding more testing. I can see the work put into creating round-robin-test.lc and this would require more time spent developing tests for this assignment.

3. This assignment ended up being due the Sunday after finals on Dec 20, 2020. The last thing I would want is to put more work on the plate of students who already have a busy finals week. I would hope that if any additions were made to round-robin.lc that this would be taken into account. I think it would have been nice to have received this assignment as soon as the weekend before finals started so that we have time to get started and process the assignment in our heads.
