# Workshop Exercise Solutions

## First Steps

### Exercise 1

1. `26`
2. `36`
3. Type error: `Couldn't match expected type ‘Float’ with actual type ‘Int’`

### Exercise 2

Inferred type: `square :: Num a => a -> a`

### Exercise 3

```
showResult x = "The result is " ++ show x
```

### Exercise 4

```
showAreaOfCircle r = "The area of a circle with radius " 
                     ++ show r ++ "cm is about " 
                     ++ show (2 * r * pi) ++ " cm^2"
```

## Fundamentals

### Exercise 1

Conditional:
```
sort2 :: Ord a => a -> a -> (a, a)
sort2 x y = if x <= y then (x, y) else (y, x)
```

Guards:
```
sort2 :: Ord a => a -> a -> (a, a)
sort2 x y | x <= y    = (x, y)
          | otherwise = (y, x)
```

(The solution using guards is more idiomatic in Haskell.)

### Exercise 2

```
isLower :: Char -> Bool
isLower ch = ch >= 'a' && ch <= 'z'
```

### Exercise 3

```
mangle :: String -> String
mangle (x:xs) = xs ++ [x]
mangle []     = []
```

### Exercise 4

```
divide :: Int -> Int -> Int
divide x y = length [x, 2*x..y]
```

