---
title: Call Python Function by Dynamical Name
author: Yan Zhang
date: 2020-10-31 6:55:00 +0800
categories: [Tutorial]
tags: [Python]
pin: true
---

## Sample

```python
def func1():
    print(2)

def func2():
    print(2):

def func3():
    print(3)

func_list = ["func1", "func2", "func3"]

for func_name in func_list:

    # execute function by function name
    globals()[func_name]()

# output:
# 1
# 2
# 3
```
