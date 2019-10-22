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

Bowles 2.2: <br/>Classification Problems: <br/>Detecting Unexploded Mines Using Sonar
=========

```python
import pandas as pd
import numpy as np
import os
fileDir = os.path.dirname(os.path.realpath('__file__'))
print("Loakles Verzeichnis: ", fileDir)
```

## Listing 2-1: Sizing Up a New Data Setâ€”rockVmineSummaries.py




CSV einlesen: Anders als Bowles machen wir das mit Pandas.

Doku: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html

```python
# Bowles Listing 2-1: Sizing Up a New Data Setâ€”rockVmineSummaries.py
# dataSource = "https://archive.ics.uci.edu/ml/machine-learning-databases/undocumented/connectionist-bench/sonar/sonar.all-data"
source_csv_file = "../data/sonar.all-data.csv"
source_csv_file = os.path.join(fileDir, source_csv_file)
source_df = pd.read_csv(source_csv_file, header=None)
print("Eingelesen aus\n%s:\n%i Zeilen, %i Spalten" % (source_csv_file,source_df.shape[0], source_df.shape[1] ))
```

```python
# number of rows, colums
source_df.shape
```

## Listing 2-2: Determining the Nature of Attributesâ€”rockVmineContents.py

```python
# datatypes of cols
source_df.info(verbose=True)
```

## Listing 2-3: Summary Statistics for Numeric and Categorical Attributesâ€”rVMSummaryStats.py

```python
(nrow, ncol) = source_df.shape
print(source_df.shape)
print("rows: %i, cols: %i" % (nrow, ncol))
print("total number of measurements:", source_df.size)
```

Bowles berechnet die gÃ¤ngigen statistischen KenngrÃ¶ÃŸen manuell, z.B.:

    colMean = np.mean(colArray); colsd = np.std(colArray)
    
Pandas stellt dazu die Methode ``describe()`` bereit - siehe unten Listing 2.4.



Unique Werte in der 61ten Spalte (weil der Index mit 0 beginnt also Spalte 60) mit Pandas.

Doku: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.unique.html

```python
#hide XXX
source_df[60].unique()

```

Oder a la Bowles nativ mit Python als Menge oder Liste:

```python
colData = source_df[60]
unique = set(colData)
print("unique Werte als Menge: ", unique)
```

```python
#count up the number of elements having each value
catDict = dict(zip(list(unique),range(len(unique))))
catCount = [0]*2
for elt in colData:
   catCount[catDict[elt]] += 1
print("unique Werte als Liste: ", list(unique))
print("catCount dazu:          ", catCount )

```

## Listing 2-5: Using Python Pandas to Read and Summarize Dataâ€”pandasReadSummarize.py

https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.describe.html#pandas.DataFrame.describe

```python
#hide XXX
#print XXX and tail of data frame
display(source_df.describe())
display(source_df.tail(2))

```

```python
#hide XXX
# Deskriptive Statistik 08/15    
source_df.info() # erfasst standardmÃ¤ÃŸig nur die numerischen Attribute
```

Auch Zusammenfassungen von nicht-numerischen Attributen sind mÃ¶glich:

```python
#hide XXX
source_df.describe(include=XXX)
```
