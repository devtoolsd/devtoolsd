---
name: NumPy
slug: numpy
language: python
description: Fundamental array computing library for Python — the backbone of the entire scientific Python ecosystem.
logo: https://upload.wikimedia.org/wikipedia/commons/3/31/NumPy_logo_2020.svg
website: https://numpy.org
github: numpy/numpy
year: 2005
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: data
tags: [scientific-computing, arrays, math, python, data-science, linear-algebra]
related_frameworks: [pandas, scipy, pytorch]
features:
  - "N-dimensional arrays (`ndarray`) as the universal data container"
  - "Vectorised operations — replace loops with fast C/Fortran kernels"
  - "Broadcasting — operate on arrays of different shapes without loops"
  - "Linear algebra: `np.linalg` for matrix operations, eigenvalues, solvers"
  - "Random number generation with seeded reproducibility"
  - "Fast Fourier transforms via `np.fft`"
  - "Integration with Pandas, SciPy, scikit-learn, PyTorch, TensorFlow"
  - "Memory-mapped arrays for datasets too large to fit in RAM"
install:
  pip: "pip install numpy"
  conda: "conda install numpy"
---

NumPy provides multi-dimensional arrays and a library of mathematical operations that run in optimised C and Fortran code. It is the common data exchange format of the scientific Python stack — Pandas, SciPy, scikit-learn, PyTorch, and TensorFlow all interoperate with NumPy arrays. Vectorised operations over arrays replace explicit Python loops, giving 10–100× speedups for numerical work.

## Quick start

```bash
pip install numpy
```

```python
import numpy as np

# Create arrays
a = np.array([1, 2, 3, 4, 5])
b = np.arange(1, 6)              # [1, 2, 3, 4, 5]
c = np.zeros((3, 4))             # 3x4 matrix of zeros
d = np.random.rand(3, 3)         # 3x3 matrix of random floats

# Vectorised operations (no loop needed)
print(a * 2)                     # [2, 4, 6, 8, 10]
print(a + b)                     # [2, 4, 6, 8, 10]
print(a.mean(), a.std())

# 2D array operations
matrix = np.array([[1, 2], [3, 4]])
print(matrix.T)                  # transpose
print(np.linalg.det(matrix))     # determinant: -2.0
print(np.linalg.inv(matrix))     # inverse

# Broadcasting
x = np.array([[1, 2, 3],
               [4, 5, 6]])
print(x + np.array([10, 20, 30]))  # add row-wise

# Boolean indexing
scores = np.array([72, 45, 88, 91, 60])
print(scores[scores > 70])          # [72, 88, 91]
```

## When to use

NumPy is essential for any Python numerical or scientific computing work. It's a dependency of virtually every data science library and you'll use it even when working at higher levels (Pandas, PyTorch). Use NumPy directly for linear algebra, signal processing, and custom numerical algorithms. For tabular data and time series, Pandas adds labelled indexing on top. For GPU-accelerated array computing, CuPy provides a NumPy-compatible API.
