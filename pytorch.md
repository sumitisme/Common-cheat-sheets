# <span style="color:green">Pytorch Cheat sheet</span>

---

## Use Jupyter Notebook when using pytorch and pandas, it's much more convenient.

---

# IMPORTING PYTORCH

---

```py

# MAIN STUFF

# Root package
import torch

# Neural Networks
import torch.nn as nn


# EXTRA STUFF

# Popular image datsets, architectures and transforms
from torchvision import datasets, models, transforms

# Collection of layers, activations and more
import torch.nn.functional as F            
```
---

# EXTRA STUFF AFTER IMPORTS 

---

## Checking version

```py
print(f"PyTorch version: {torch.__version__}")
```
---

## Some intro regarding neural networks

```py
# Almost everything in PyTorch is called a "Module"
# Neural Networks are built by stacking Modules together

This_is_a_module = nn.Linear(in_features = 1, out_features = 1)

print(type(this_is_a_module))
# Will print out 
# <class 'torch.nn.modules.linear.Linear'>
```
---

# DATA IMPORTS

---

```py
# Import PyTorch Dataset (You can store your data here) and DataLoader (You can load your data here)
from torch.utils.data import Dataset, DataLoader
```