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

Bowles 2.1: The Anatomy of a New Problem
=========

```python
import pandas as pd
import numpy as np
```

CSV einlesen mit Pandas
----

```python
import os
fileDir = os.path.dirname(os.path.realpath('__file__'))
fileDir
```

Doku: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html

```python
## Bowles Listing 2-1: Sizing Up a New Data Setâ€”rockVmineSummaries.py
## dataSource = "https://archive.ics.uci.edu/ml/machine-learning-databases/undocumented/connectionist-bench/sonar/sonar.all-data"
#source_csv_file = os.path.join(fileDir, "../data/sonar.all-data.csv")
#source_df = pd.read_csv(source_csv_file, header=None) 
```

```python
# Titanic Dataset
# dataSource = MLPC bitly
source_csv_file = "../data/titanic_MLPC.csv"
# ggf. auch so:
# source_csv_file = os.path.join(fileDir, "../data/titanic_MLPC.csv")

source_df = pd.read_csv(source_csv_file,
                # header=0  # default: column names are inferred from the first line of the file 
                )
```

```python
source_df
```

```python
# Hierbei handelt es sich um einen Unit-Test welcher die Input-Daten auf Konformität mit dem zu verwendenden Algorithmus überprüft. Falls ein unbekanntes Format vorliegt, dann wird diese Methode einen Fehler werfen!
assert isinstance(source_df, (pd.pandas.core.frame.DataFrame))
```

FAQ: CSV anders einlesen, z.B. mit Numpy? Antwort: NEIN. Pandas ``read_csv()`` ist am schnellsten, Alternativen sind schlechter. 

Diskussion unter
https://stackoverflow.com/questions/3518778/how-do-i-read-csv-data-into-a-record-array-in-numpy : """I tested code similar to this with a csv file containing 2.6 million rows and 8 columns. numpy.recfromcsv() took about 45 seconds, np.asarray(list(csv.reader())) took about 7 seconds, and pandas.read_csv() took about 2 seconds (!). (The file had recently been read from disk in all cases, so it was already in the operating system's file cache.) I think I'll go with pandas""" (Kommentar Matthias Fripp Mar 31 '16 at 21:56)




einen ersten Eindruck gewinnen
---

Die ersten und letzten paar Zeilen anschauen, die man eingelesen hat: 
   * https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.head.html
   * https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.tail.html


```python
## Die ersten paar Zeilen anschauen
source_df.head()
```

```python
## die letzten 3 Zeilen anschauen
source_df.tail(3)
```

Zusammenfassende Informationen: 
   * https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.info.html


```python
## concise summary: Datentypen, Anzahl Items ungleicht Null, Memory
source_df.info(verbose=True)
```

Beschreibende Statistik: die Ã¼blichen 08/15-Informationen
----

   * https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.describe.html#pandas.DataFrame.describe


```python
#hide XXX
# Deskriptive Statistik 08/15    
source_df.describe()
```

```python
#hide XXX
source_df.describe(include='all')
```

Der Datensatz in Numpy
----



```python
#hide XXX
# dataframe in Numpy n-dimensionales Array konvertieren
source_ndarray = source_df.values
assert isinstance(source_ndarray, np.ndarray)
```

FÃ¼r uns interessante Attribute der Klasse https://numpy.org/devdocs/reference/generated/numpy.ndarray.html :
  * size
  * ndim
  * shape
  * T

```python
print(source_df.shape, source_ndarray.shape)
```

```python

```
