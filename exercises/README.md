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
