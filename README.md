# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1.Start the program, import the required NumPy and Sys libraries, and get the order n of the matrix as input.

2.Initialize the augmented matrix a and solution array x with zeros. Read the augmented matrix elements from the user.

3.Perform Gaussian elimination to convert the augmented matrix into an upper triangular matrix. Check for zero diagonal elements to avoid division by zero, then use back substitution to calculate the unknown values.

4.Display the calculated values of the variables in the format X0, X1, ... up to two decimal places and Stop the program.

## Program:
```
'''Program to solve a matrix using Gaussian elimination without partial pivoting.
Developed by: CHANDRU V
RegisterNumber: 212224230043
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
import sys

# Reading number of unknowns
n = int(input())

# Making numpy array of n x n+1 size and initializing 
# to zero for storing augmented matrix
a = np.zeros((n,n+1))

# Making numpy array of n size and initializing 
# to zero for storing solution vector
x = np.zeros(n)

# Reading augmented matrix coefficients
for i in range(n):
    for j in range(n+1):
        a[i][j] = float(input())

# Applying Gauss Elimination
for i in range(n):
    if a[i][i] == 0.0:
        sys.exit('Divide by zero detected!')
        
    for j in range(i+1, n):
        ratio = a[j][i]/a[i][i]
        
        for k in range(n+1):
            a[j][k] = a[j][k] - ratio * a[i][k]

# Back Substitution
x[n-1] = a[n-1][n]/a[n-1][n-1]

for i in range(n-2,-1,-1):
    x[i] = a[i][n]
    
    for j in range(i+1,n):
        x[i] = x[i] - a[i][j]*x[j]
    
    x[i] = x[i]/a[i][i]

# Displaying solution
for i in range(n):
    print('X%d = %0.2f' %(i,x[i]), end = ' ')
```

## Output:

<img width="845" height="487" alt="image" src="https://github.com/user-attachments/assets/40fe216a-2576-478a-bf08-c7da145f0a9f" />



## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

