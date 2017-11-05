---
layout: page
title: Python program to illustrate different set operations.
permalink: /ai/lab-4/
---
```python
a=[1,2,3,4]
b=[3,4,5,6]
print "a=",a;print "b=",b
print "operations"
c=list(set(a)|set(b))
print "union operation  ",c
d=list(set(a)&set(b))
print "intersection operation  ",d
e=list(set(a)-set(b))
print "difference operation  ",e
f=list(set(a)^set(b))
print "symmetric operation  ",f
```
## Python program to generate Calendar for the given month and year.
```python
import calendar
a=input("enter year ")
b=input("enter month ")
cal=calendar.month(a,b)
print "calender"
print cal
```
## Python program to implement Simple Calculator program.
```python
def add(x, y):
   return x + y

def sub(x, y):
   return x - y

def mul(x, y):
   return x * y

def div(x, y):
   return x / y

print("Select operation.")
print("1.Add")
print("2.Sub")
print("3.Mul")
print("4.Div")

choice = input("Enter choice(1/2/3/4):")

num1 = int(input("Enter first number: "))
num2 = int(input("Enter second number: "))

if choice == '1':
   print(num1,"+",num2,"=", add(num1,num2))

elif choice == '2':
   print(num1,"-",num2,"=", sub(num1,num2))

elif choice == '3':
   print(num1,"*",num2,"=", mult(num1,num2))

elif choice == '4':
   print(num1,"/",num2,"=", div(num1,num2))
else:
   print("Invalid input")
```
