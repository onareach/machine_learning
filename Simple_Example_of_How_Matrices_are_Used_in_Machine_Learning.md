# Super Simple Example of How Matrices are Used in Machine Learning



#### Student Grade Prediction Example

Let's say we want to predict student grades based on the number of hours each student sleeps and the number of hours they study.

Let's say we have only the following data for three students:

|      | Hours Studied | Hours of Sleep | Score |
| ---- | ------------- | -------------- | ----- |
| 1    | 2             | 7              | 13    |
| 2    | 5             | 5              | 20    |
| 3    | 8             | 3              | 27    |

Based on this data, our ML modest learns that:

Each hour of study is worth 3 points.

Each hour of sleep is worth 1 point.



#### How the Model Works (Matrix Multiplication)

We represent the students' data as matrix X:

## Matrix Representation in Markdown

The matrix **X** is defined as:

## Matrix Representation in Markdown

The matrix **X** is defined as:

$X = \begin{bmatrix} 2 & 7 \\ 5 & 5 \\ 8 & 3 \end{bmatrix}$

### Explanation:

- `\[` and `\]` start and end the **LaTeX block** for displaying the matrix.
- `\begin{bmatrix} ... \end{bmatrix}` defines a **matrix with brackets**.
- Each row is written **on a new line**, with values separated by `&`.

This works in **Markdown editors that support LaTeX**, such as:

- Jupyter Notebook
- GitHub Markdown (via `$` inline math mode)
- Obsidian
- Some static site generators (like MkDocs)

