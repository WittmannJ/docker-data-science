---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

dsci_intro_1
====

Quelle (ggf. in einem anderen Fenster Ã¶ffnen): https://learnxinyminutes.com/docs/python3/ ;

Vorgehen: Quellcode download von https://learnxinyminutes.com/docs/files/learnpython3.py und hier in Jupyter in einem neuen Tab/Fenster Ã¶ffnen.


```python
# Integer division rounds down for both positive and negative numbers.
-5 // 3      # => -2
```

```python
# pointer vs. values
# (XXX vs. ==)  checks if two variables refer to the same object, but == checks
# if the objects pointed to have the same values.
a = [1, 2, 3, 4]  # Point a at [1, 2, 3, 4]
b = a             # Point b at what a points to
print(b is a)            # => True, a and b refer to the same object
print(b == a)            # => True, a's and b's objects are equal
b = [1, 2, 3, 4]  # Point b at [1, 2, 3, 4]
print(b is a)            # => False, a and b do not refer to the same object
print(b == a)            # => True, a's and b's objects are equal
```

```python

```
