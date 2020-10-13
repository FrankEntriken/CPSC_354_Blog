# Week 1, Beginning Haskell

### My specifications
MacOS Catalina 10.15.6

.zsh shell terminal (https://ohmyz.sh/)

### How I installed Haskell

`
curl -sSL https://get.haskellstack.org/ | sh
ghci
`

I used to run Haskell in the default bash terminal, this process was slightly different:

`
curl -sSL https://get.haskellstack.org/ | sh
stack exec ghci
`

There may be a requirement depending on your computer where the developer tools for Mac needs to be downloaded in order to run 'stack exec ghci'

### Getting Started

Everytime I use a new language I like to toy around with its most basic functions in order to learn the syntax and other differences that make the language unique

`
Prelude> 1 + 1
2
Prelude> 1 - 2
-1
Prelude> 1  +1
2
Prelude> 9*   2
18
Prelude> 9/3
3.0
Prelude> 
`

What does this teach me?
1. Haskell supports standard mathematical functions such as addition, subtraction, multiplation, and divison as well as negative numbers
2. Haskell does not constrain the spacing between numbers when using these functions which makes me think that the language does not have many restrictions

Moving forward, these observations will shape how I write in Haskell
