---
layout: post
title: Exchange paradox
published: true
---
Code:

```python
a, b = 0, 1
while b < 10:
    print(b)
    a, b = a, a + b
```
