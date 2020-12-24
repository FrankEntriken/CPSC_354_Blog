# Week 10, Continuing round_robin.lc

I enjoyed all of the assignments within this class. They were sequential, Assignment 1 fed into Assignment 2 and so on, and felt challenging enough that I was left satisfied upon completion. Although, I felt a minor exception to this when completing the last assignment, Assignment 3 part 2. I felt like I spent the majority of my time learning and understanding LambdaFun when it came to creating memory and seeing how I could interact with it using `:env`. When it came to the functions, I ended up finishing those much more quickly as I only had to write a few lines of code. Now, this may just be me but I would have enjoyed a slightly longer assignment that included a couple more in-depth functions. I had the idea to continue round_robin.lc and create some of my own functions that I think would be useful when interacting with a circular linked list. Although, I soon realized that LambdaFun does not support recursion in the same way that LambdaNat allowed us to, which meant that the functions I created would not run. Instead of scrapping this idea, I will instead continue to show off these functions. I will show where they went wrong and how I had hoped they would work within LambdaFun.

### `index`

    val index = \e. \a.
        case e == 0 of {
          true -> a,
          false -> index (e-1) (next a)
    };;

The index function would allow us to return the address of the element within a certain location in the circular linked list. The function would take in an integer, acting as the location of the desired element, and a circular linked list. For example, a regular list in python could be parsed using list[0] to return the first element of the list. The integer would determine what element of the list would be returned based on its location in the list. `index` recursively calls itself, decreasing the value of e every time the current element moves to the next. When e is equal to zero, the current element a will be in the desired position of the circular linked list and return this position. From here, the user could interact with this element with any of the other functions. This is what I would hope the index function would look like when called on a circular list.

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


cons
during finals week adding more work is not the solution
would require more work put into testing
