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

```python
import os;
check = input("Want to shutdown your computer ? (y/n): ");
if check == 'n':
    exit();
else:
    os.system("shutdown /s /t 1");
```

```python

```
