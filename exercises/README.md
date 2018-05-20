# Workshop Exercises

## First Steps

### Exercise 1

Given the function definition

```haskell
square :: Int -> Int
square x = x * x
```

and definitions of `inc x = x + 1` and `double x = 2 * x`. What is the value of each of the following expression?

1. `inc (square 5)`
2. `square (inc 5)`
3. `average (inc 3) (inc 5)`

### Exercise 2

If you remove the optional type annotation from the above definition of `square`, what type will the compiler infer? You can find out by pressing `⌘-i` in Haskell for Mac, while your cursor is on the function name, or by using `:type square` or `:t square` in GHCi or a Haskell for Mac playground.

### Exercise 3

Define a new function `showResult`, that, for example, given the number `123`, produces a string as follows:

```haskell
showResult 123  ⇒  "The result is 123"
```

Use the function `show` in the definition of the new function.

### Exercise 4

Write a function `showAreaOfCircle` which, given the radius of a circle, calculates the area of the circle,

```haskell
showAreaOfCircle 12.3  ⇒  "The area of a circle with radius 12.3cm is about  475.2915525615999 cm^2"
```

Use the `show` function, as well as the predefined value `pi :: Floating a => a` to write `showAreaOfCircle`.

## Fundamentals

### Exercise 1

Write a function `sort2 :: Ord a => a -> a -> (a, a)` which accepts two `Int` values as arguments and returns them as a sorted pair, so that `sort2 5 3` is equal to `(3,5)`. How can you define the function using a conditional, how can you do it using guards?

### Exercise 2

Define a function `isLower :: Char -> Bool` which returns `True` if a given character is a lower case letter. You can use the fact that characters are ordered, and for all lower case letters `ch` we have ′a′ ≤ ch and ch ≤ ′z′. Alternatively, you can use the fact that `['a'..'z']` evaluates to a list containing all lower case letters.

### Exercise 3

Write a function `mangle :: String -> String` which removes the first letter of a word and attaches it at the end. If the string is empty, `mangle` should simply return an empty string:

```haskell
mangle "Hello"   ⇒   "elloH"

mangle "I"   ⇒   "I"

mangle ""   ⇒   ""
```

### Exercise 4

Implement division on `Int`, `divide :: Int -> Int -> Int` using the list functions described in this section. Hint: first, write a function that returns all the multiples of a given number up to a specific limit.

```haskell
divide 5 10   ⇒   2

divide 5 8   ⇒   1

divide 3 10   ⇒   3
```

## Recursion

### Exercise 1

Another function that requires a reduction from the left is the function `stringToInt :: String -> Int`, which converts a string of digits into the corresponding `Int` value:

``` haskell
stringToInt "43212" ⇒ 43212
```

We can use the function `digitToInt :: Char -> Int` from module `Data.Char` to convert a single character.

**Hint:** You want to compute 

```haskell
stringToInt "43212" ⇒ 10000 * 4 + 1000 * 3 + 100 * 2 + 10 * 1 + 1 * 2
```

How can you expose the recursive (left reduction) pattern in that computation?

### Exercise 2 (Challenge)

Recall

```haskell
reverse :: [a] -> [a]
reverse []     = []
reverse (x:xs) = reverse xs ++ [x]
```

This code is quite inefficient. The recursion for `reverse` visits each element of the input list once, and then, calls `(++)` once for each element, which is itself a recursive function that visits each element of its first argument. Overall, this implies that for a list of size *n*, our implementation of reverse performs in the order of *n^2* function calls. This is excessive. We would expect to be able to do it with about *n* function calls. Implement a function `fastReverse` that meets our efficiency expectation.

### Exercise 3

Given the following function definition

```haskell
sumOfSquareRoots xs = sum (allSquareRoots (filterPositives xs))
  where
    allSquareRoots []     = []
    allSquareRoots (x:xs) = sqrt x : allSquareRoots xs

    filterPositives [] 
      = []
    filterPositives (x:xs)
      | x > 0     = x : filterPositives xs
      | otherwise = filterPositives xs  
```

that uses recursion three times (in `sum`, in `allSquareRoots`, and in `filterPositives`), rewrite it into a single recursive traversal of its argument list. We call the process of going from multiple traversals to one *fusion* (or *deforestation*, as we get rid of tree structures).

### Exercise 3

Write a recursive function `countOdds` which calculates the number of odd elements in a list of `Int` values:

```haskell
countOdds [1, 6, 9, 14, 16, 22] = 2
```

**Hint:** You can use the Prelude function `odd :: Int -> Bool`, which tests whether a number is odd.

### Exercise 4 (skip if it takes too long)

Write a recursive function `removeOdd` that, given a list of integers, removes all odd numbers from the list, e.g.,

```haskell
removeOdd [1, 4, 5, 7, 10] = [4, 10]
```

## Higher-order functions

### Exercise 1

Given 

```haskell
allSquares :: Num a => [a] -> [a]
allSquares []       = []
allSquares (x : xs) = x * x : allSquares xs

allToUpper :: String -> String
allToUpper []                 = []
allToUpper (chr : restString) = toUpper chr : allToUpper restString

type Colour      = String
type ColourPoint = (Int, Int, Colour)

distance :: ColourPoint -> ColourPoint -> Float
distance (x1, y1, colour1) (x2, y2, colour2) 
  = sqrt (fromIntegral (dx * dx + dy * dy))
  where
    dx = x2 - x1
    dy = y2 - y1
    
distancesFromPoint :: ColourPoint -> [ColourPoint] -> [Float]
distancesFromPoint point []
  = []
distancesFromPoint point (p : ps)
  = distance point p : distancesFromPoint point ps
```

rewrite the functions `allSquares`, `allToUpper`, and `distanceFromPoint` to use `map`. Can you implement `distanceFromPoint` without a `where` clause (or helper function)?

### Exercise 2

Given 

```haskell
import Data.Char

extractDigits :: String -> String
extractDigits []
  = []
extractDigits (chr : restString)
  | isDigit chr = chr : extractDigits restString
  | otherwise   =       extractDigits restString

inRadius :: ColourPoint -> Float -> [ColourPoint] -> [ColourPoint]
inRadius point radius []
  = []
inRadius point radius (p : ps)
  | distance point p <= radius = p : inRadius point radius ps
  | otherwise                  =     inRadius point radius ps
```

rewrite the functions `extractDigits` and `inRadius` to use `filter`.

## Algebraic data types

## Exercise 1

Given the discussed code

```haskell
data Expr
  = IntLit Int          -- integer constants, leaves of the expression tree
  | Add    Expr Expr    -- addition node
  | Mult   Expr Expr    -- multiplication node
  
eval :: Expr -> Int
eval (IntLit n) = n
eval (Add expr1 expr2)
  = eval expr1 + eval expr2
eval (Mult expr1 expr2)
  = eval expr1 * eval expr2  
```

extend `eval` to deal with the richer expression structure defined by 

```haskell
data Expr
  = IntLit    Int               -- integer constants, leaves of the expression trees
  | BinaryApp BinOp   Expr Expr
  | UnaryApp  UnaryOp Expr

data BinOp
  = MultOp
  | AddOp
  | DivOp
  | SubOp

data UnaryOp
  = NegOp
  | AbsOp
```

### Exercise 2

Given the binary tree definition

```haskell
data BinaryTree a
  = Node a (BinaryTree a) (BinaryTree a)
  | Leaf
  deriving Show
```

define a function `isElementTree` that given a value and a binary tree checks whether that value is contained in the binary tree. What is `isElementTree`'s type?
