# Super Simple Example of How Matrices are Used in Machine Learning



#### Student Grade Prediction Example

Let's say we want to predict student grades based on the number of hours each student sleeps and the number of hours they study.

Let's say we have only the following data for three students:

|      | Hours Studied | Hours of Sleep | Predicted Score |
| ---- | ------------- | -------------- | --------------- |
| 1    | 2             | 7              | 13              |
| 2    | 5             | 5              | 20              |
| 3    | 8             | 3              | 27              |

Based on this data, our ML modest learns that:

Each hour of study is worth 3 points.

Each hour of sleep is worth 1 point.



#### How the Model Works (Matrix Multiplication)

We represent the students' data as a matrix **X**:

$$
X =
\begin{bmatrix}
2 & 7 \\
5 & 5 \\
8 & 3
\end{bmatrix}
$$


We represent the weights (influence of study and sleep) as another matrix **W**:
$$
X =
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
This gives the predictors scores for each student.



#### Why Is This Important?

- All ML models use matrices to **store** and **process data**.
- Neural networks (so-called) are just big stacks of matrix multiplications.
- Instead of manually programming if-else rules, ML models glean the best weights  **W** from data.



### **Expanding This into Training a Machine Learning Model**

Now that we understand **how matrices are used for predictions**, let’s expand this into **training a model** using **Linear Regression**.



### **The Core Idea: Training Means Learning the Best Weights**

- In our previous example, we manually set the weights (W = [3, 1]), meaning we *assumed* studying was worth 3 points per hour and sleeping was worth 1.
- But what if we don’t know the best weights? "Training a model" means finding the best values for **W** so that the predictions match real data as closely as possible.

To do this, we need:

1. **A dataset**: Features **X** and actual results **Y** (true scores).
2. **A loss function**: Measures how far off our predictions are.
3. **Gradient Descent**: Adjusts **W** to minimize the loss.



### **Training the Model**

Let’s break this down mathematically and using Python.

#### **Step 1: The Dataset**

We now introduce **real test scores** (**Y**):

| Hours Studied | Sleep Hours | Actual Score (Y) |
| ------------- | ----------- | ---------------- |
| 2             | 7           | **15**           |
| 5             | 5           | **22**           |
| 8             | 3           | **26**           |

Now, instead of assuming weights (**W**), we will "train" the model to find the best values.



#### Step 2: Define a Prediction Function

The model makes predictions using:

$$
\hat{Y} = X \times W
$$

where:

- **X** is our **feature matrix** (hours studied & sleep).
- **W** is our **weight matrix** (what we need to learn).
- **Y (with a hat)** is the **predicted score**.



#### Step 3: Define a Loss Function (Mean Squared Error)

To measure how bad our predictions are, we use:

$$
\text{Loss} = \frac{1}{n} \sum (\hat{Y} - Y)^2
$$

where:

- **Y** is the **actual test score**.
- **Y (with a hat)** is the **predicted test score**.
- The **squared difference** punishes large mistakes more.



#### **Step 4: Train Using Gradient Descent**

- We **start with random weights**.
- We **adjust** **W** using **gradient descent** to minimize the loss.
- This process **repeats** until the loss is small.



### **Results from Python**

|      | Hours Studied | Sleep Hours | Actual Score | Predicted Score |
| ---- | ------------- | ----------- | ------------ | --------------- |
| 1    | 2             | 7           | 15           | 15.500000004    |
| 2    | 5             | 5           | 22           | 21.0            |
| 3    | 8             | 3           | 26           | 26.499999996    |



Here’s the result of **training the model** using **gradient descent**.

### **How the Training Process Worked:**

1. We started with **random weights**.
2. The model made **predictions** using matrix multiplication.
3. We calculated the **error (loss)** between the predictions and actual scores.
4. The model **adjusted the weights** slightly in each iteration to reduce the error.
5. After **1000 iterations**, the model found **optimal weights** that produce better predictions.

### **Final Predictions:**

- **Student 1** (2 hrs studied, 7 hrs sleep): Actual = **15**, Predicted = **15.5**
- **Student 2** (5 hrs studied, 5 hrs sleep): Actual = **22**, Predicted = **21.0**
- **Student 3** (8 hrs studied, 3 hrs sleep): Actual = **26**, Predicted = **26.5**

The model **learned** the best relationship between studying, sleep, and scores!



### Python Code (Simple and Refined)

##### 1.  Create a Python venv and install numpy, pandas, and mpmath.

First, we'll use a simple approach.

##### 2.  Create a file called ml.py in the venv with the following code:

    import numpy as np
    import pandas as pd
    
    # Step 1: Define the dataset (X = features, Y = actual results)
    X = np.array([
        [2, 7],   # Student 1: 2 hours studied, 7 hours of sleep
        [5, 5],   # Student 2: 5 hours studied, 5 hours of sleep
        [8, 3]    # Student 3: 8 hours studied, 3 hours of sleep
    ])
    
    Y = np.array([15, 22, 26]).reshape(-1, 1)  # Actual test scores
    
    # Step 2: Initialize weights randomly
    np.random.seed(42)  # For reproducibility
    W = np.random.rand(2, 1)  # 2 features, 1 output
    
    # Step 3: Define the learning rate and number of iterations
    learning_rate = 0.01
    iterations = 1000
    
    # Step 4: Train using Gradient Descent
    n = len(Y)  # Number of samples
    loss_history = []
    
    for i in range(iterations):
        # Step 4.1: Make predictions
        Y_pred = np.dot(X, W)
        
        # Step 4.2: Compute Mean Squared Error (Loss)
        loss = np.mean((Y_pred - Y) ** 2)
        loss_history.append(loss)
        
        # Step 4.3: Compute the Gradient (Derivative of Loss wrt W)
        gradient = (2/n) * np.dot(X.T, (Y_pred - Y))
        
        # Step 4.4: Update Weights using Gradient Descent
        W -= learning_rate * gradient
    
    # Step 5: Display Final Weights and Predictions
    df = pd.DataFrame(X, columns=["Hours Studied", "Sleep Hours"])
    df["Actual Score"] = Y.flatten()
    df["Predicted Score (Final)"] = np.dot(X, W).flatten()
    
    print(df)
    

##### 3.  Output from the Previous Code:

    (output)
    
    (venv_ml) $ python ml.py
       Hours Studied  Sleep Hours  Actual Score  Predicted Score (Final)
    0              2            7            15                     15.5
    1              5            5            22                     21.0
    2              8            3            26                     26.5



The following is a high-precision approach to the same calculation:

##### 4.  Create a file called ml.py in the venv with the following code:

    import numpy as np
    import pandas as pd
    from mpmath import mp
    
    # Set mpmath precision to 50 decimal places
    mp.dps = 50  
    
    # Step 1: Define dataset with high precision
    X = np.array([
        [mp.mpf(2), mp.mpf(7)],  
        [mp.mpf(5), mp.mpf(5)],  
        [mp.mpf(8), mp.mpf(3)]   
    ], dtype=object)  
    
    Y = np.array([
        mp.mpf(15), 
        mp.mpf(22), 
        mp.mpf(26)
    ], dtype=object).reshape(-1, 1)  
    
    # Step 2: Initialize weights randomly
    np.random.seed(42)  
    W = np.array([
        [mp.mpf(np.random.rand())], 
        [mp.mpf(np.random.rand())]
    ], dtype=object)  
    
    # Step 3: Define hyperparameters
    learning_rate = mp.mpf("0.00001")  
    iterations = 100000  
    
    # Step 4: Train using Gradient Descent
    n = len(Y)  
    loss_history = []
    
    for i in range(iterations):
        # Predictions
        Y_pred = np.dot(X, W)  
        
        # Convert to mpmath objects
        Y_pred = np.array([mp.mpf(val) for val in Y_pred.flatten()], dtype=object).reshape(-1, 1)
        Y_actual = np.array([mp.mpf(val) for val in Y.flatten()], dtype=object).reshape(-1, 1)
    
        # Compute Mean Squared Error (Loss)
        loss = mp.fsum([mp.power(val, 2) for val in (Y_pred - Y_actual).flatten()]) / n
        loss_history.append(loss)
        
        # Compute Gradient
        gradient = (2/n) * np.dot(X.T, (Y_pred - Y_actual))
        
        # Update Weights
        W -= learning_rate * gradient  
        
        # Display training progress
        if (i + 1) % (iterations // 10) == 0:
            print(f"Training Progress: {(i + 1) / iterations * 100:.2f}% completed")
    
    print("Training complete!\n")
    
    # Step 5: Display Final Predictions
    df = pd.DataFrame(X, columns=["Hours Studied", "Hours of Sleep"])
    df["Actual Score"] = Y.flatten()
    df["Predicted Score (Final)"] = np.dot(X, W).flatten()
    
    # Print results with full precision
    pd.set_option("display.float_format", lambda x: f"{x:.20f}")
    print(df)
    
    



##### 5.  Output from the Previous Code:

    (output)
    
    (venv_ml) $ python ml.py
    Training Progress: 10.00% completed
    Training Progress: 20.00% completed
    Training Progress: 30.00% completed
    Training Progress: 40.00% completed
    Training Progress: 50.00% completed
    Training Progress: 60.00% completed
    Training Progress: 70.00% completed
    Training Progress: 80.00% completed
    Training Progress: 90.00% completed
    Training Progress: 100.00% completed
    Training complete!
    
      Hours Studied Hours of Sleep Actual Score     Predicted Score (Final)
    0           2.0            7.0         15.0     15.500000320857230777342510761046446...
    1           5.0            5.0         22.0     21.000000023732376996491509613141111...
    2           8.0            3.0         26.0     26.499999726607523215640508465235775...


