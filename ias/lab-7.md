---
layout: page
title: Generate random numbers using LCG.
permalink: /ias/lab-7/
---
## LCG
```python
def seedLCG(initVal):
	global rand
	rand=initVal
def lcg():
	global rand
	rand=(a*rand+c)%m
	return rand
x0=int(input('enter seed value'))
seedLCG(x0)
a=int(input('enter a value'))
c=int(input('enter c value'))
m=int(input('enter m value'))
print x0
for i in range(0,10):
	print(lcg())
```
## Blum Blum Shub
```python
from random import randint
import math
def gcd(ii,jj):
    if ii==0:
     return jj
    else:
     return gcd(jj%ii,ii)


p=int(input('enter p value'))
q=int(input('enter q value'))
if(p%4==3 & q%4==3):
	n=p*q
else:
	print 'enter p and q value whose remainder is 3 when divided by 4'
	p=int(input('enter p value'))
	q=int(input('enter q value'))
	n=p*q
s=int(input('enter s value'))
while s<n:
  if (gcd(s,n)==1):
    break
  else:
    s=s+1
x=(s*s)%n   
for i in range(10):
  x=(x*x)%n
  bits=x%2
  print bits
```
