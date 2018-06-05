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

## Recursion

### Exercise 1

```
import DataChar

stringToInt :: String -> Int
stringToInt str = stringToIntAcc 0 str
  where
    stringToIntAcc :: Int -> String -> Int
    stringToIntAcc acc []
       = acc
    stringToIntAcc acc (chr : restString) 
       = stringToIntAcc (10 * acc + digitToInt chr) restString
```

### Exercise 2

```
fastReverse :: [a] -> [a]
fastReverse xs = reverseAcc [] xs
  where
    reverseAcc :: [a] -> [a] -> [a]
    reverseAcc accList []     = accList
    reverseAcc accList (x:xs) = reverseAcc (x : accList) xs
 ```
 
 ### Exercise 3
 
```
sumOfSquareRoots [] 
  = 0
sumOfSquareRoots (x:xs)
  | x > 0     = sqrt x + sumOfSquareRoots xs
  | otherwise = sumOfSquareRoots xs   
```

### Exercise 4

```
countOdds [] = 0
countOdds (x:xs) | odd x     = 1 + countOdds xs
                 | otherwise = countOdds xs
```

### Exercise 5

```
removeOdd [] = []
removeOdd (x:xs) | odd x     = removeOdd xs
                 | otherwise = x : removeOdd xs
```

## Higher-order functions

### Exercise 1

```
import Data.Char

allSquares :: Num a => [a] -> [a]
allSquares xs = map square xs
  where
    square x = x * x

allToUpper :: String -> String
allToUpper string = map toUpper string

type Colour      = String
type ColourPoint = (Int, Int, Colour)

distancesFromPoint :: ColourPoint -> [ColourPoint] -> [Float]
distancesFromPoint point points = map distanceP points
  where
    distanceP :: ColourPoint -> Float
    distanceP p = distance point p
```

### Exercise 2

```
import Data.Char

extractDigits :: String -> String
extractDigits strings = filter isDigit strings

inRadius :: ColourPoint -> Float -> [ColourPoint] -> [ColourPoint]
inRadius point radius points = filter inRadiusP points
  where
    inRadiusP :: ColourPoint -> Bool
    inRadiusP p = distance point p <= radius
```
