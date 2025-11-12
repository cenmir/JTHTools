# JTHTools

Tools for teaching linear algebra and finite element methods (FEM) in marimo notebooks. Provides LaTeX rendering for NumPy arrays with clean syntax.

## Installation

Install directly from GitHub:

```bash
pip install git+https://github.com/cenmir/JTHTools.git
```

For local development, install in editable mode:

```bash
uv pip install -e .
```

## Usage

```python
import numpy as np
from jthtools import la

# Pipe syntax (recommended)
np.array([1, 2, 3]) | la

# Function call syntax
la(np.array([1, 2, 3]))

# Works with expressions
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])
(A @ B) | la

# Scalars, vectors, and matrices all work
np.dot([1, 2, 3], [4, 5, 6]) | la
```

## Features

- **Automatic LaTeX rendering** for NumPy arrays in marimo notebooks
- **Scalars, vectors (1D), and matrices (2D)** are all supported
- **Intelligent truncation** for large arrays (>8 elements/dimension)
- **Clean pipe syntax** for readable code: `array | la`
- **Format preservation** for integers, floats (2 decimals), and complex numbers

## Example Output

Vectors with ≤5 elements display as column vectors:
```
[1]
[2]
[3]
```

Large matrices automatically truncate with ellipsis notation:
```
[1  2  3  ...  10]
[11 12 13 ... 20]
⋮   ⋮   ⋮   ⋱   ⋮
[91 92 93 ... 100]
```

## Why the Wrapper?

NumPy's `ndarray` is a C-defined immutable type that cannot have display methods added at runtime. Marimo also doesn't provide a public API for registering formatters for third-party types. The pipe syntax `| la` is the cleanest solution for opt-in LaTeX rendering.


## Development

This allows editing the source code and have the changes immediately reflected in the environment, which is perfect for development.   

```
uv pip install -e ./JTHTools
```