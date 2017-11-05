---
layout: page
title: Python program to implement Modulo Multiplicative Inverse.
permalink: /ias/lab-1/
---
```python
def inverseMod(a, m):
    for i in range(1,m):
        if ( m*i + 1) % a == 0:
            return ( m*i + 1) // a
    return None

a = input("Input a number of \"a\": ")
b = input("Input a number of \"b\": ")

print("The Modular inverses of %s modulo %s is %s" % (a, b, inverseMod(a,b)))
```
## Python program to implement Logical operators.

```python
x = False
y = False

# Output: x and y is False
print('x and y is',x and y)


# Output: x or y is True
print('x or y is',x or y)


# Output: not x is False
print('not x is',not x)
```

## Python program to implement Modular Arithmetic.

```python
a = input("Input a number of \"a\": ")
b = input("Input a number of \"b\": ")
c=a%b
print("The Modular  of %s modulo %s is %s" % (a,b,c))
```
