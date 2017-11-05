---
layout: page
title: Python program to print multiplication table of a given number
permalink: /ai/lab-1a/
---
```python
num=int(input())
for i in range(1, 11):
   print(num,'x',i,'=',num*i)
```
## Python program to check whether the given number is prime or not.
```python
num = int(input("Enter a number: "))
if num > 1:
   # check for factors
   for i in range(2,num):
       if (num % i) == 0:
           print(num,"is not a prime number")
           print(i,"times",num//i,"is",num)
           break
   else:
       print(num,"is a prime number")
else:
   print(num,"is not a prime number")
```
## Python program to find factorial of the given number.
```python
num = int(input("Enter a number: "))
factorial = 1
if num < 0:
   print("Sorry, factorial does not exist for negative numbers")
elif num == 0:
   print("The factorial of 0 is 1")
else:
   for i in range(1,num + 1):
       factorial = factorial*i
   print("The factorial of",num,"is",factorial)
```
