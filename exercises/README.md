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
