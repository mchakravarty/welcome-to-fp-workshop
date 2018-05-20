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
