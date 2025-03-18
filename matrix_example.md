## How the Model Works (Matrix Multiplication)

We represent the students' data as a **matrix** $X$:

$$
X =
\begin{bmatrix}
2 & 7 \\
5 & 5 \\
8 & 3
\end{bmatrix}
$$

We represent the **weights** (influence of study and sleep) as another **matrix** $W$:

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

This gives the **predicted scores** for each student.
