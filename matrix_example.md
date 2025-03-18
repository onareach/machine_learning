## Matrix Representation in Markdown

The matrix **X** is defined as:

$$
X =
\begin{bmatrix}
2 & 7 \\
5 & 5 \\
8 & 3
\end{bmatrix}
$$

## Matrix Representation in Markdown

The matrix **X** is defined as:

$$
X =
\begin{bmatrix}
2 & 7 \\
5 & 5 \\
8 & 3
\end{bmatrix}
$$

The weight matrix **W** is:

$$
W =
\begin{bmatrix}
3 \\
1
\end{bmatrix}
$$

To make predictions, we multiply these matrices:

$$
X \times W =
\begin{bmatrix}
(2 \times 3) + (7 \times 1) \\
(5 \times 3) + (5 \times 1) \\
(8 \times 3) + (3 \times 1)
\end{bmatrix}
=
\begin{bmatrix}
13 \\
20 \\
27
\end{bmatrix}
$$

### Explanation:
- `$$ ... $$` is used for **block math mode** (GitHub and Jupyter Notebook support this).
- `\begin{bmatrix} ... \end{bmatrix}` defines a **matrix with brackets**.
- Each row is written **on a new line**, with values separated by `&`.

This works in **Markdown editors that support LaTeX**, such as:

- Jupyter Notebook
- GitHub Markdown (via `$$` inline math mode)
- Obsidian
- Some static site generators (like MkDocs)

## Matrix Representation in Markdown

The matrix **X** is defined as:

$$
X =
\begin{bmatrix}
2 & 7 \\
5 & 5 \\
8 & 3
\end{bmatrix}
$$

The weight matrix **W** is:

$$
W =
\begin{bmatrix}
3 \\
1
\end{bmatrix}
$$

To make predictions, we multiply these matrices:

$$
X \times W =
\begin{bmatrix}
(2 \times 3) + (7 \times 1) \\
(5 \times 3) + (5 \times 1) \\
(8 \times 3) + (3 \times 1)
\end{bmatrix}
=
\begin{bmatrix}
13 \\
20 \\
27
\end{bmatrix}
$$

### Step 2: Define a Prediction Function
The model makes predictions using:

$$
\hat{Y} = X \times W
$$

where:
- \( X \) is our **feature matrix** (hours studied & sleep).
- \( W \) is our **weight matrix** (what we need to learn).
- \( \hat{Y} \) is the **predicted score**.

### Step 3: Define a Loss Function (Mean Squared Error)
To measure how bad our predictions are, we use:

$$
\text{Loss} = \frac{1}{n} \sum (\hat{Y} - Y)^2
$$

where:
- \( Y \) is the **actual test score**.
- \( \hat{Y} \) is the **predicted test score**.
- The **squared difference** punishes large mistakes more.

### Explanation:
- `$$ ... $$` is used for **block math mode** (GitHub and Jupyter Notebook support this).
- `\begin{bmatrix} ... \end{bmatrix}` defines a **matrix with brackets**.
- Each row is written **on a new line**, with values separated by `&`.

This works in **Markdown editors that support LaTeX**, such as:

- Jupyter Notebook
- GitHub Markdown (via `$$` inline math mode)
- Obsidian
- Some static site generators (like MkDocs)



To make predictions, we multiply these matrices:

$$
X \times W =
\begin{bmatrix}
(2 \times 3) + (7 \times 1) \\
(5 \times 3) + (5 \times 1) \\
(8 \times 3) + (3 \times 1)
\end{bmatrix}
=
\begin{bmatrix}
13 \\
20 \\
27
\end{bmatrix}
$$
