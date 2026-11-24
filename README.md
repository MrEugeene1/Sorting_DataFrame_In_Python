<div align="center">

# 📍 Sorting a DataFrame with Pandas

**A short, hands-on guide to sorting data by one or more columns and resetting the index afterwards.**

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Level](https://img.shields.io/badge/Level-Beginner-2ea44f?style=for-the-badge)

</div>

---

## 📖 Overview

Sorting is one of the most common steps in data analysis: ranking, ordering and tidying data before you report on it.
This notebook covers how to sort a Pandas `DataFrame` with **`sort_values()`**, from a simple single-column sort to a multi-column sort with mixed order, and how to clean up the index with **`reset_index()`**.

## 🎯 What You'll Learn

| # | Topic | Key Method / Parameter |
|:-:|-------|------------------------|
| 1 | Sort by a single column | `sort_values(by=[...])` |
| 2 | Sort by several columns | `by=['col1', 'col2']` |
| 3 | Mix ascending and descending order | `ascending=[True, False]` |
| 4 | Keep the sorted result | `inplace=True` |
| 5 | Reset a shuffled index | `reset_index()` |
| 6 | Drop the old index column | `reset_index(drop=True)` |

## 📂 Project Structure

```
1. Sorting the DataFrame/
├── 1. Sorting the DataFrame.ipynb   # Step-by-step notebook
└── README.md                        # You are here
```

## 🧪 Sample Dataset

The notebook builds a small DataFrame of students:

| roll_no | name    | grade | marks | city      |
|:-------:|---------|:-----:|:-----:|-----------|
| 102     | Aravind | B     | 15    | Gurugram  |
| 101     | Rahul   | B     | 15    | Delhi     |
| 104     | Prateek | A     | 20    | Delhi     |
| 103     | Piyuesh | C     | 4     | Gurugram  |
| 105     | Kartik  | A     | 22    | Hyderabad |

## 🚀 Walkthrough

### 1️⃣ Sort by a single column

```python
data_frame.sort_values(by=['grade'])
```

Students are grouped by grade (A → C), but students who share a grade are not ranked by marks.

### 2️⃣ Sort by several columns in mixed order

```python
data_frame.sort_values(by=['grade', 'marks'], ascending=[True, False])
```

Grades go **ascending**, and within each grade marks go **descending**, so the top scorer comes first.

| roll_no | name    | grade | marks | city      |
|:-------:|---------|:-----:|:-----:|-----------|
| 105     | Kartik  | A     | 22    | Hyderabad |
| 104     | Prateek | A     | 20    | Delhi     |
| 102     | Aravind | B     | 15    | Gurugram  |
| 101     | Rahul   | B     | 15    | Delhi     |
| 103     | Piyuesh | C     | 4     | Gurugram  |

### 3️⃣ Keep the sorted result

`sort_values()` returns a **new** DataFrame and leaves the original unchanged. To change the original, either reassign it or use `inplace=True`:

```python
data_frame.sort_values(by=['grade', 'marks'], ascending=[True, False], inplace=True)
```

### 4️⃣ Reset the index

After sorting, the index keeps its old order (`4, 2, 0, 1, 3`). Reset it with:

```python
data_frame.reset_index()                          # keeps old index as an 'index' column
data_frame.reset_index(drop=True, inplace=True)   # discards the old index
```

## ⚡ Quick Reference

```python
df.sort_values(by='col')                                   # ascending, single column
df.sort_values(by='col', ascending=False)                  # descending
df.sort_values(by=['a', 'b'], ascending=[True, False])     # multi-column, mixed order
df.sort_values(by='col', inplace=True)                     # modify in place
df.reset_index(drop=True)                                  # clean 0..n-1 index
```

> 💡 **Tip:** Prefer `df = df.sort_values(...)` over `inplace=True` in production code. It is easier to chain and to read.

## 🛠️ Getting Started

**Prerequisites:** Python 3.8+ and pip.

```bash
# 1. Install dependencies
pip install pandas jupyter

# 2. Launch Jupyter
jupyter notebook "1. Sorting the DataFrame.ipynb"
```

You can also open the notebook directly in **VS Code** (with the Jupyter extension) or upload it to **Google Colab**.

## 📚 Further Reading

- [pandas.DataFrame.sort_values](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_values.html)
- [pandas.DataFrame.reset_index](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reset_index.html)
- [pandas.DataFrame.sort_index](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_index.html)

---

<div align="center">

⭐ If you found this helpful, consider giving it a star!

</div>
