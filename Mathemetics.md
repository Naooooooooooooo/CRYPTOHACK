# Mathemetics

First challenge told us to calculate `gcd(a,b)` for `a = 66528`, `b = 52920`

We use `math.gcd()` function in python

```py
import math

a = 66528
b = 52920

print(math.gcd(a,b))
```

Result 

>1512

The second challenge gives us two primes `p = 26513`, `q = 32321` and we have to find the integers `u`,`v` such that

`p * u + q * v = gcd(p,q)` the lower number is the flag

I use `Extended Euclidean algorithms` stolen from [here](https://www.geeksforgeeks.org/python-program-for-basic-and-extended-euclidean-algorithms-2/)

```py
# Python program to demonstrate working of extended
# Euclidean Algorithm
	
# function for extended Euclidean Algorithm
def gcdExtended(a, b):
	# Base Case
	if a == 0 :
		return b,0,1
			
	gcd,x1,y1 = gcdExtended(b%a, a)
	
	# Update x and y using results of recursive
	# call
	x = y1 - (b//a) * x1
	y = x1
	
	return gcd,x,y
	

# Driver code
a, b = 26513, 32321
g, x, y = gcdExtended(a, b)
print(x,' ',y)



```

The result

>10245   -8404

Third challenge told us to calculate

>11 ≡ x mod 6

>8146798528947 ≡ y mod 17

The number smaller is the flag


To get `x` and `y` we use `%` operator

```py
x = 11 % 6
y= 8146798528947 % 7

print(x,' ',y)
```

Output
>5 1

So the flag is 
> 1

The fourth challenge told us to Calculate `273246787654^65536 mod 65537` and `65537` is prime

`273246787654` is not divided by `65537` and `65536` is `phi(65537)`

Euler'theorem

![Euler'theorem](./euler_theorem)

So the answer is `1`

The last challenge told us to find `d` that `3 * d ≡ 1 mod 13`

We find `a`, `b` that `a * 13  + b * 3  = 1`

So `a * 13  + b * 3  mod 13  = 1 mod 13`, and `a * 13 mod 13 = 0`

Then `b * 3 mod 13 = 1 mod 13`

So we use `extended Euclidean Algorithm` to calculate `d`

We have `d = -4`



