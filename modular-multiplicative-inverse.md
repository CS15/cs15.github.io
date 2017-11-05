---
layout: page
permalink: /lab-1/
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
