# Week 2, Learning Haskell

### Loading files

Files can be loaded within Haskell using

`:load file_name`

Once the file is loaded, the functions that are established within the file will now be available to the user

    -- numbers
    data NN = O | S NN
        deriving (Eq,Show)

    -- addition
    add :: NN -> NN -> NN
    add O n = n
    add (S n) m = S (add n m)
    -- add (S O) (S (S O))
